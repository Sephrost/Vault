La grammatica presenta 2 produzioni non disgiunte, quindi aggiungiamo una produzione $Statp\to else<stat>|\epsilon$ e modifichiamo quella corrente 
#### First
$FIRST(Prog)=\{assign,print,read,while,if,\{\}$
$FIRST(Statlist)=\{assign,print,read,while,if,\{\}$
$FIRST(Statlistp)=\{;\}$
$FIRST(Stat)=\{assign,print,read,while,if,\{\}$
$FIRST(Idlist)=\{Id\}$
$FIRST(Idlistp)=\{,\}$
$FIRST(Bexp)=\{Relop\}$
$FIRST(Expr)=\{+,-,*,/,Num,Id\}$
$FIRST(Exprlist)=\{+,-,*,/,Num,Id\}$
$FIRST(Exprlistp)=\{,\}$
$FIRST(Statp)=\{else\}$
#### Follow
$\$\in FOLLOW(Prog)$
$EOF\in FOLLOW(Statlist)$
$FOLLOW(Statlist)\subseteq FOLLOW(Statlistp)$
$FIRST(Statlistp)\in FOLLOW(Stat)$
$FOLLOW(Statlist)\subseteq FOLLOW(Stat)$
$FOLLOW(Statlistp)\subseteq FOLLOW(Stat)$
$to \in FOLLOW(expr)$
$)\in FOLLOW(Exprlist),FOLLOW(Idlist),FOLLOW(Bexpr)$
$FOLLOW(Stat)\subseteq FOLLOW(Idlist)$
$end \in FOLLOW(Stat)$
$else \in FOLLOW(Stat)$
$\}\in FOLLOW(Statlist)$
$FIRST(Expr)\in FOLLOW(Expr)$
$FOLLOW(Idlist)\subseteq FOLLOW(Idlistp)$
$FOLLOW(Bexpr)\subseteq FOLLOW(expr)$
$FIRST(Exprlistp)\in FOLLOW(Expr)$
$FOLLOW(Exprlist)\subseteq FOLLOW(Exprlistp)$
$EOF \in FOLLOW(Statp)$
Var|Follow
--|--
Prog|$\$$
Statlist|$\},EOF$
Statlistp|$\},EOF$
Stat|$else,and,\},EOF,;$
Idlist|$),else,and,\},EOF,;$
Idlistp|$),else,and,\},EOF,;$
Bexpr|$)$
Expr|$to,),+,-,*,/,Num,Id$
Exprlist|$)$
Exprlistp|$)$
Statp|$a$

#### Insiemi guida
$GUIDA(<Prog>\to<Statlist>EOF)=\{assign,print,read,while,if,\{\}$
$GUIDA(<Statlist>\to<Stat><Statlistp>)=\{assign,print,read,while,if,\{\}$
$GUIDA(<Statlistp>\to;<Stat><Statlistp>)=\{;\}$
$GUIDA(<Statlistp>\to \epsilon)=FOLLOW(Statlistp)=\{\},EOF\}$
$GUIDA(<Stat>\to assign<expr>to<idlist>)=\{assign\}$
$GUIDA(<Stat>\to print(<exprlist>))=\{print\}$
$GUIDA(<Stat>\to read(<idlist>))=\{read\}$
$GUIDA(<Stat>\to while(<bexpr>)<stat>)=\{while\}$
$GUIDA(<Stat>\to if(<bexpr>)<stat><Statp>end)=\{if\}$
$GUIDA(<Stat>\to \{<Statlist>\})=\{\{\}$

$GUIDA(<Idlist>\to Id<Idlistp>)=\{Id\}$

$GUIDA(<Idlistp>\to,Id<Idlistp>)=\{,\}$
$GUIDA(<Idlistp>\to \epsilon)=FOLLOW(Idlistp)\{),else,and,\},EOF,;\}$

$GUIDA(<Bexpr>\to Relop<Expr><Expr>)=\{Relop\}$

$GUIDA(<Expr>\to +(<Exprlist>))=\{+\}$
$GUIDA(<Expr>\to *(<Exprlist>))=\{*\}$
$GUIDA(<Expr>\to -<Expr><Expr>)=\{-\}$
$GUIDA(<Expr>\to /<Expr><Expr>)=\{/\}$
$GUIDA(<Expr>\to Num)=\{Num\}$
$GUIDA(<Expr>\to Id)=\{Id\}$
$Guida(Exprlist \to <Expr><Exprlistp>)=\{+,-,*,/,Num,Id\}$

$Guida(<Exprlistp>\to ,<Expr><Exprlistp>)=\{,\}$
$Guida(<Exprlistp>\to \epsilon)=\{)\}$

$Guida(Statp\to else<stat>)=\{else\}$
$Guida(Statp\to \epsilon)=\{EOF\}$