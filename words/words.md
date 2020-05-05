<div class="section">
    <div>
    	<iframe id="splash" width="960" height="480" src="banners/splash.html"></iframe>
        <div style="top: 70px;font-size: 75px;font-weight: bold;">
        	O Que Acontece em Seguida?
       	</div>
		<div style="font-weight: 500;top: 140px;left: 10px;font-size: 29px;">
			COVID-19, Futuros Explicados com Simulações
		</div>
		<div style="font-weight: 100;top: 189px;left: 10px;font-size: 19px;line-height: 21px;">
			<b>
				🕐 Leitura/Simulações em 30 min
				&nbsp;&middot;&nbsp;
			</b>
			por
			<a href="https://scholar.google.com/citations?user=_wHMGkUAAAAJ&amp;hl=en">Marcel Salathé</a>
			(epidemiologista)
			&
			<a href="https://ncase.me/">Nicky Case</a>
			(artista/programador)
		</div>
	</div>
</div>

"A única coisa a temer é o próprio medo" é um conselho estúpido.

Claro, não junte papel higiênico - mas se os governantes temem o próprio medo eles irão minimizar os reais perigos de "pânico em massa". O medo não é o problema, mas, sim, como nós *canalizamos* nosso medo. O medo nos dá energia para lidar com os perigos agora, e se preparar para os perigos mais à frente.

Honestamente, nós (Marcel, epidemiologista + Nicky, artista/programador) estamos preocupados. Nós podemos apostar que você está também! Por isto nós canalizamos nosso medo para criar estas **simulações lúdicas**, para que *você* possa canalizar seu medo para entender:

* **Os Últimos Meses** (epidemiologia 101, modelo SEIR, R & R<sub>0</sub>)
* **Os Próximos Meses** (lockdowns, rastreamento de contato, máscaras)
* **Os Próximos Anos** (perda de imunidade? sem vacinas?)

Este guia (publicado em 1º de Maio de 2020. clique nesta nota de rodapé!→[^timestamp]) visa trazer para você esperança *e* medo. Para derrotar o COVID-19 **de uma forma que também proteja nossa saúde mental e financeira**, nós precisamos de otimismo para criar planos, e pessimismo para criar planos emergenciais. Como Gladys Bronwyn Stern disse uma vez, *"O otimista inventa o avião e o pessimista o paraquedas."*

[^timestamp]: Estas notas de rodapé terão fontes, links ou comentário bônus. Como este comentário!
    
	**Este guia foi publicado em 1º de maio de 2020.** Muitos detalhes irão se tornar desatualizados, mas nós estamos confiantes que o guia cobrirá 95% dos futuros possíveis, e que Epidemiologia 101 será útil para sempre.

Então, apertem os cintos: nós estamos prestes a experimentar alguma turbulência.

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Os Últimos Meses</div>
    </div>
</div>

Pilotos usam simuladores de vôo para aprender a não destruir aviões.

**Epidemiologistas usam simuladores epidêmicos para aprender como não destruir a humanidade.**

Então, vamos construir um "simulador de vôo epidêmico" muito, muito simples!, <icon i></icon> Nesta simulação, pessoas infectadas podem tornar <icon s></icon> Pessoas suscetíveis em mais <icon i></icon>Pessoas infectadas:

![](pics/spread.png)

É estimado que, *no início* do surto de COVID-19, o vírus passa de uma <icon i></icon> para uma <icon s></icon> a cada 4 dias, *em média*. [^serial_interval] (lembre-se, há muita variação)

[^serial_interval]: “The mean [serial] interval was 3.96 days (95% CI 3.53–4.39 days)”. [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article) (Disclaimer: Early release articles are not considered as final versions)

Se nós simularmos "dobra a cada 4 dias" *e nada mais*, em uma população, começando com apenas 0.001% <icon i></icon>, o que acontece? 

**Clique "Iniciar" para rodar a simulação! Você pode rodar outras vezes com outros parâmetros:**
(ressalvas técnicas:[^caveats])

[^caveats]: **Lembre-se: todas estas simulações são super simplificadas, para propósitos educacionais.**
	Uma simplificação: Quando você pede que a simulação "Infecte 1 nova pessoa a cada x dias", ele de fato está aumentando o número de infectados 1/x a cada dia. O mesmo ocorre para os demais ajustes destas simulações.
	- "Recuperar a cada x dias" está de fato reduzindo o número de infectados 1/x a cada dia.
    
	Estas *não são* exatamente as mesmas coisas, mas são próximas o suficiente, e para propósitos educacionais é menos obscuro que ajustar as taxas de transmissão e recuperação diretamente.

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-1" width="800" height="540"></iframe>
</div>

Esta é a **curva de crescimento exponencial.** Começa pequena, e então explode. "Oh é apenas uma gripe"para "Tá certo, gripes não criam *cemitérios de valas comuns em cidades ricas*".

![](pics/exponential.png)

Mas, esta simulação está errada. O crescimento exponencial, ainda bem, não pode ser perpétuo. Uma razãopara impedir o espalhamento do vírus é se outras pessoas *já* tem o vírus:

![](pics/susceptibles.png)

Quanto mais <icon i></icon>s existem, mais rápido <icon s></icon>s se tornam <icon i></icon>s, **mas quanto menos <icon s></icon>s existem, mais *lentamente* <icon s></icon>s se tornam <icon i></icon>s.**

Como isto muda o crescimento de uma epidemia? Vamos descobrir:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-2" width="800" height="540"></iframe>
</div>

Esta é a **curva de crescimento logístico.** em formato de S. Começa devagar, explode, e desacelera de novo.

Mas, esta simulação *ainda* está errada. Nós estamos esquecendo o fato que <icon i></icon>Pessoas infectadas em algum momento param de ser infecciosas, seja 1) se recuperando, 2)"se recuperando" com dano aos pulmões, ou 3) morrendo.


Por questão de simplicidade, vamos fingir que todas as <icon i></icon> Pessoas infectadas se tornem <icon r></icon> Recuperadas. (Apenas lembrem-se que na realidade algumas morrem.) <icon r></icon>s não podem ser infectadas de novo, e vamos assumir – *por enquanto!* – que se tornam imunes por toda a vida.

No caso da COVID-19, é estimado que você permaneça <icon i></icon> Infectado por 10 dias, *em média*.[^infectiousness] Isto significa que alguns vão se recuperar antes de 10 dias e outros depois. **Este é o resultado, com uma simulação *começando* com 100% <icon i></icon>:**

[^infectiousness]: "A mediana do período contagioso \[...\] era de 9.5 dias.” [Hu, Z., Song, C., Xu, C. et al](https://link.springer.com/article/10.1007/s11427-020-1661-4) Sim nós sabemos que "mediana" não é igual a "média". Para o propósito educacional simplificado é perto o suficiente.


<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-3" width="800" height="540"></iframe>
</div>

Isto é o oposto do crescimento exponencial, a **curva de decaimento exponencial.**

Agora, o que acontece se você simular crescimento logístico em formato de S *com* a recuperação?

![](pics/graphs_q.png)

Vamos descobrir.

<b style='color:#ff4040'>Curva vermelha</b> são os casos *atuais*<icon i></icon>,    
<b style='color:#999999'>Curva cinza</b> é o *total* de casos (atuais + recuperados <icon r></icon>), 
que se inicia em apenas 0.001% <icon i></icon>:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-4" width="800" height="540"></iframe>
</div>

E é *daí* que esta famosa curva veio! Não é uma curva em sino, e não é nem mesmo uma curva "log-normal". Ela não tem nome. Mas você já deve ter visto um zilhão de vezes, e torcido muito para que ela achatasse.

Este é o **Modelo SIR**,[^sir]    
(<icon s></icon>**S**uscetível <icon i></icon>**I**nfectado <icon r></icon>**R**ecuperado)      
a *segunda* idéia mais importante em Epidemiologia 101:

[^sir]: Para mais explicações técnicas do Modelo SIR, veja [the Institute for Disease Modeling](https://www.idmod.org/docs/hiv/model-sir.html#) e [Wikipedia](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SIR_model)

![](pics/sir.png)

**NOTA: A simulações que informam as políticas são muito, *muito* mais sofisticadas que isto!** Mas o Modelo SIR ainda serve para encontrarmos as mesmas conclusõesgerais, mesmo que deixando passar algumas nuances.

De fato, vamos acrescentar uma nuance adicional: antes de um <icon s></icon> se tornar <icon i></icon>, ele primeiro se torna <icon e></icon> Exposto. Isto é quando ele tem o vírus mas ainda não pode passar adiante - infec*tado* mas não infec*cioso*.

![](pics/seir.png)

(Esta variante é chamada o  **Modelo SEIR**[^seir], onde o "E" significa <icon e></icon> "Exposto". Note que este *não é* o significado usual de "exposto", em que você pode ou não ter o vírus. Nesta definição técnica "Exposto" significa que você definitivamente tem. A terminologia científica é ruim.)

[^seir]: Para mais explicações técnicas do Modelo SEIR, veja [the Institute for Disease Modeling](https://www.idmod.org/docs/hiv/model-seir.html) e [Wikipedia](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology#The_SEIR_model)


No caso da COVID-19, é estimado que você fique <icon e></icon> infectado-mas-não-infeccioso por 3 dias, *em média*.[^latent] O que acontece se adicionarmos isto à simulação?

[^latent]: “Assumindo uma distribuição do período de incubação de 5.2 dias, em média, resultado de um estudo em separado dos primeiros casos de COVID-19, nós inferimos que o contágio começa a partir de 2.3 dias ((95% IC, 0.8-3.0 dias) antes dos sintomas se instalarem." (traduzindo: assumindo que os sintomas começam no dia 5, o contágio começa 2 dias antes = contágio começa no dia 3) [He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)

<b style='color:#ff4040'>Curva Vermelha</b> <b style='color:#FF9393'>+ Rosa</b> são os casos *atuais* (infeccioso <icon i></icon> + exposto <icon e></icon>),    
<b style='color:#888'>Curva cinza</b> são casos *totais* (atuais + recuperados <icon r></icon>):

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-5" width="800" height="540"></iframe>
</div>
Não há muitas mudanças! O tempo que você permanece <icon e></icon> Exposto muda a razão de <icon e></icon>-para-<icon i></icon>, e *quando* os casos correntes atingem o pico... mas a *altura* do pico, e o total de casos no final, permanecem os mesmos.

Por que isto acontece? Por causa da mais importante idéia em Epidemiologia 101:

![](pics/r.png)

Abreviação de "Número de reprodução". É o número *médio* de pessoas que um <icon i></icon> infecta *antes* de se recuperar (ou morrer).

![](pics/r2.png)

**R** muda durante o curso de um surto, já que ganhamos mais imunidade e intervenções.


**R<sub>0</sub>** (pronounced R-nought) is what R is *at the start of an outbreak, before immunity or interventions*. R<sub>0</sub> more closely reflects the power of the virus itself, but it still changes from place to place. For example, R<sub>0</sub> is higher in dense cities than sparse rural areas.

(Most news articles – and even some research papers! – confuse R and R<sub>0</sub>. Again, science terminology is bad)

The R<sub>0</sub> for "the" seasonal flu is around 1.28[^r0_flu]. This means, at the *start* of a flu outbreak, each <icon i></icon> infects 1.28 others *on average.* (If it sounds weird that this isn't a whole number, remember that the "average" mom has 2.4 children. This doesn't mean there's half-children running about.)

[^r0_flu]: “The median R value for seasonal influenza was 1.28 (IQR: 1.19–1.37)” [Biggerstaff, M., Cauchemez, S., Reed, C. et al.](https://bmcinfectdis.biomedcentral.com/articles/10.1186/1471-2334-14-480)

The R<sub>0</sub> for COVID-19 is estimated to be around 2.2,[^r0_covid] though one *not-yet-finalized* study estimates it was 5.7(!) in Wuhan.[^r0_wuhan]

[^r0_covid]: “We estimated the basic reproduction number R0 of 2019-nCoV to be around 2.2 (90% high density interval: 1.4–3.8)” [Riou J, Althaus CL.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7001239/)

[^r0_wuhan]: “we calculated a median R0 value of 5.7 (95% CI 3.8–8.9)” [Sanche S, Lin YT, Xu C, Romero-Severson E, Hengartner N, Ke R.](https://wwwnc.cdc.gov/eid/article/26/7/20-0282_article)

Nas nossa simulações – *no início & na média* – um <icon i></icon> infecta alguém a cada 4 dias, em 10 dias. "4 dias" ocorre dentro de "10 dias" duas vezes e meia. Isto significa – *no início & na média* – cada <icon i></icon> infecta 2.5 outros. Então, R<sub>0</sub> = 2.5. (ressalvas:[^r0_caveats_sim])

[^r0_caveats_sim]: Isto é assumindo que você é igualmente infeccioso durante todo o "período infeccioso". Mais uma vez simplificações para propósitos educacionais.

**Brinque com esta calculadora de R<sub>0</sub>, para ver como  R<sub>0</sub> depende dos tempos de recuperação e nova infecção:**

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-6a&format=calc" width="285" height="255"></iframe>
</div>

But remember, the fewer <icon s></icon>s there are, the *slower* <icon s></icon>s become <icon i></icon>s. The *current* reproduction number (R) depends not just on the *basic* reproduction number (R<sub>0</sub>), but *also* on how many people are no longer <icon s></icon> Susceptible. (For example, by recovering & getting natural immunity.)

Mas lembre-se, quanto menos <icon s></icon>s há, mais *lentamente* <icon s></icon>s tornam-se <icon i></icon>s. O número de reprodução (R) *corrente* depende não apenas do número de reprodução *básico* (R<sub>0</sub>), mas *também* em quantas pessoas não são mais <icon s></icon> Suscetíveis. (Por exemplo, por se recuperar e conseguindo imunidade natural.)

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-6b&format=calc" width="285" height="390"></iframe>
</div>

When enough people have immunity, R < 1, and the virus is contained! This is called **herd immunity**. For flus, herd immunity is achieved *with a vaccine*. Trying to achieve "natural herd immunity" by letting folks get infected is a *terrible* idea. (But not for the reason you may think! We'll explain later.)
Quando pessoas suficientes tem imunidade, R < 1, e o vírus é contido! Isto é chamado **imunidade de rebanho**. Para gripes, a imunidade de rebanho é atingida *com uma vacina*. Tentando atingir "imunidade de rebanho natural" deixando as pessoas se infectarem é uma idéia *terrível*. (Mas não pelas razões que você pode pensar! Explicaremos mais a frente.)

Vamos rodar o Modelo SEIR outra vez, mas mostrando R<sub>0</sub>, R ao longo do tempo, e o limiar de imunidade de rebanho:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=epi-7" width="800" height="540"></iframe>
</div>

**NOTA: O total de casos *não para* na imunidade de rebanho, mas ultrapassa ele!** E ele cruza o limiar *exatamente* quando os casos correntes atingem o pico. (Isto acontece não importa como você mude os ajustes - tente você mesmo!)

Isto ocorre porque quando há mais não-<icon s></icon>s do que o limiar da imunidade de rebanho, você tem R < 1. E quando R < 1, novos casos param de crescer: um pico.

**Se houver apenas uma lição para você tirar deste guia é esta** - é um diagrama extremamente complexo, então tome um tempo para absorvê-lo completamente:

![](pics/r3.png)

**Isto significa: nós NÃO precisamos impedir todas as transmissões, ou nem mesmo algo próximo de todas as transmissões, para parar o COVID-19!**

É um paradoxo. COVID-19 é extremamente contagioso, porém para contê-lo, nós "só" precisamos impedir 60% das infecções. 60%?! Se fosse uma nota no boletim seria um D-. Mas se R<sub>0</sub> = 2.5, cortando isto por 61% nós temos R = 0.975, que é R < 1, vírus contido! (fórmula exata:[^exact_formula])

[^exact_formula]: Lembre-se R = R<sub>0</sub> * a proporção das transmissões ainda permitidas. Lembre-se ainda que a proporção das transmissões ainda permitidas = 1 - proporção das transmissões  *impedidas*.
    
    Logo, para ter R < 1, você precisa ter R<sub>0</sub> * TransmissõesPermitidas < 1. 
    
    Logo, TransmissõesPermitidas < 1/R<sub>0</sub>
    
    Logo, 1 - TransmissõesImpedidas < 1/R<sub>0</sub>
    
    Logo, TransmissõesImpedidas > 1 - 1/R<sub>0</sub>
    
    Logo, você precisa parar mais que **1 - 1/R<sub>0</sub>** das transmissões para conseguir R < 1 e conter o vírus!  

![](pics/r4.png)

(Se você pensa que R<sub>0</sub> ou outros números nas nossas simulações são muito baixos/altos, isto é bom pois está desafiando nossas premissas! Haverá um "Modo Caixa de Areia" no fim deste guia, onde você poderá inserir os seus *próprios* números, e simular o que acontece.)

*Cada* intervenção sobre COVID-19 que você já ouviu sobre - lavar as mãos, distanciamento social/físico, lockdowns, auto-isolamento, rastreamento de contatos e quarentena, máscaras faciais, e mesmo "imunidade de rebanho" - todas estão visando a mesma coisa:

Fazer R < 1.

Então agora, vamos usar nosso "simulador de vôo epidemico" para descobrir o seguinte: Como podemos conseguir ter R < 1 de uma forma que **também proteja nossa saúde mental *e* financeira?**

Preparem-se para uma aterrisagem de emergência...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Os Próximos Meses</div>
    </div>
</div>

...poderia ter sido pior. Aqui está um universo paralelo que evitamos:

###Cenário 0: Não Fazer Absolutamente Nada

Perto de 1 em cada 20 pessoas infectadas com COVID-19 precisam ir para um UTI(Unidade de Terapia Intensiva.)[^icu_covid] Em um país rico como os EUA, há 1 cama de UTI para cada 3400 pessoas. [^icu_us] Portanto os EUA podem tratar 20 de 3400 pessoas *simultaneamente* infectadas - ou 0.6% da população.

[^icu_covid]: ["Percentage of COVID-19 cases in the United States from February 12 to March 16, 2020 that required intensive care unit (ICU) admission, by age group"](https://www.statista.com/statistics/1105420/covid-icu-admission-rates-us-by-age-group/). Entre 4.9% e 11.5% de *todos* os casos de COVID-19 requereram UTI. Generosamente escolhendo a faixa inferior, isto significa 5% ou 1 em 20. Note que este total é específico para a estrutura etária dos EUA, e será maior em países com populações mais velhas, e menor em países com populações mais jovens.

[^icu_us]: “Números de camas de UTI = 96,596”. Em [the Society of Critical Care Medicine](https://sccm.org/Blog/March-2020/United-States-Resource-Availability-for-COVID-19) População dos EUA era 328.200.000 em 2019. 96.596 de cada 328,200,000 = aproximadamente 1 em 3400. 

Mesmo se nós *mais que triplicarmos* esta capacidade para 2%, aqui está o que aconteceria *se não fizessemos absolutamente nada:*

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-1&format=lines" width="800" height="540"></iframe>
</div>

Nada bom.

Isto é o que [o relatório do Imperial College em 16 de março](http://www.imperial.ac.uk/mrc-global-infectious-disease-analysis/covid-19/report-9-impact-of-npis-on-covid-19/) descobriu: se não fizessemos nada ficaríamos sem camas de UTI, com mais de 80% da população infectada. (lembre-se: o número total de casos *ultrapassa* a imunidade de rebanho).

Mesmo se apenas 0.5% dos infectados morressem - uma suposição generosa quando não há mais vagas na UTI - em um país grande como os EUA, com 300 milhões de pessoas, 0.5% de 80% de 300 milhões = ainda são 1.2 milhões de mortos...
*SE não fizessemos nada.*

(Muitos canais de notícia e mídia social reportaram "80% serão infectados" *SEM* o "SE NÃO FIZERMOS NADA". O medo foi canalizado em clicks, e não para o entendimento. *Suspiro.*)

###Cenário 1: Achatar a Curva / Imunidade de Rebanho

O plano de "Achatar a Curva" foi apregoado por todas as organizações de saúde pública, enquanto que o plano original de "imunidade de rebanho" do Reino Unido era universalmente vaiado. Eles eram *o mesmo plano.* O Reino Unido apenas comunicou mal seu plano.[^yong]

"Ele diz que a meta real é a mesma dos outros países: achatar a curva ao escalonar o início as infecções. Como consequência, a nação deve atingir imunidade de rebanho; é um efeito colateral, e não um objetivo. [...] O verdadeiro plano de ação para o coronavírus do gorverno, disponível online, não menciona imunidade de rebanho em nenhum lugar.""
  
    Do [artigo de Ed Yong para o The Atlantic](https://www.theatlantic.com/health/archive/2020/03/coronavirus-pandemic-herd-immunity-uk-boris-johnson/608065/)

Ambos os planos, entretanto, tinham literalmente uma falha fatal.

Primeiro, vamos olhar nas duas principais formas de "achatar a curva": lavar as mãos e distanciamento físico.

O aumento da lavagem das mãos corta a incidência de gripes e resfriados em países de alta renda em ~25%[^handwashing], enquanto o lockdown de toda a cidade de Londres corta os contatos próximos em ~70%[^london]. Então, vamos assumir que a lavagem de mãos pode reduzir R *em até* 25%, e o distanciamento pode reduzir R *em até* 70%:

[^handwashing]:"Todos os oito estudos elegíveis reportaram que lavagem de mãos reduziram os riscos de infecção respiratória, com redução de riscos entre 6% a 44% [valor agrupado 24% (95% IC 6-40%)]."Nós arredondamos o valor agrupado para 25% nestas simulações por simplicidade.[Rabie, T. and Curtis, V.](https://onlinelibrary.wiley.com/doi/full/10.1111/j.1365-3156.2006.01568.x) Nota: como esta meta-análise aponta, a qualidade dos estudos para lavagem de mãos (pelo menos em países de alta renda) é péssima.

[^london]: "Nós encontramos uma redução de 73% no número de contatos diários observados por participante. Isto seria suficiente para reduzir R<sub>0</sub> de um valor de 2.6 antes do lockdown para 0.62 (0.37 - 0.89) durante o lockdown". Nós arredondamos este valor para 70% nestas simulações por simplicidade. [Jarvis and Zandvoort et al](https://cmmid.github.io/topics/covid19/comix-impact-of-physical-distance-measures-on-transmission-in-the-UK.html)

**Brinque com esta calculadora para ver qual o % de non-<icon s></icon>, lavagem de mão, e distanciamento reduzem R:** (esta calculadora visualiza os seus efeitos *relativos*, e é por isto que incrementando um *parece* como se estivessemos diminuindo o efeito de outros.[^log_caveat])

[^log_caveat]: Esta distorção sumiria se plotassemos R em uma escala logarítimca... mas então teríamos que explicar *escalas logarítimicas*

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-2a&format=calc" width="285" height="260"></iframe>
</div>

Agora, vamos simular o que acontece com uma epidemia de COVID-19 se, começando em março de 2020, nós tivessemos aumentado a lavagem de mãos mas adotado apenas *leve* distanciamento físico - de tal forma que R é mais baixo, mas ainda acima de 1:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-2&format=lines" width="800" height="540"></iframe>
</div>

Três notas:

1. Isto *reduz* o total de casos! **Mesmo se você não consegue R < 1, reduzindo R ainda salva vidas, ao reduzir o tanto que se ultrapassa sobre a imunidade de rebanho.** Muitos pensam que "Achatar a Curva" espalha os casos sem reduzir o seu número total. Isto é impossível em *qualquer* modelo em Epidemiologia 101. Mas como a mídia reportou "mais de 80% serão infectados" como inevitável, as pessoas pensam que o número total de casos será o mesmo não importando nada. *Suspiro.*

2. Devido as intervenções extra, os casos correntes atingem o pico *antes* que a imunidade de rebanho seja alcançada. De fato, nesta simulação, o número total de casos apenas ultrapass *um pouco* acimna da imunidade de rebanho - o plano do Reino Unido! Neste ponto, R < 1, você pode descartar todas as outras intervenções, e a COVID-19 permanece contida! Bem, exceto por um problema...

3. Você continua sem leitos de UTI. Por vários meses. (e lembre-se, nós *já* triplicamos as UTIs nestas simulações)

Este foi o outro achado do relatório do Imperial College em 16 de março, que convenceu o Reino Unido a abandonar o plano original. Qualquer tentativa de **mitigação** (reduzir R, mas com R>1) iria falhar. A única saída seria **supressão** (reduzir R de forma que R < 1).

![](pics/mitigation_vs_suppression.png)

Isto é, não apenas "achate" a curva, *esmague* a curva. Por exemplo, com um...

###Cenário 3: Lockdown de Meses

Vamos ver o que acontece se nós *esmagamos* a curva com um lockdown de 5 meses, reduzindo <icon i></icon> para quase nada, e então - *finalmente* - retornando para a vida normal:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-3&format=lines" width="800" height="540"></iframe>
</div>

Oh.

Esta é a "segunda onda" que todo mundo está falando a respeito. Assim que removemos o lockdown, nós voltamos a ter R > 1 de novo. Então, um único <icon i></icon> deixado para trás (ou importado) pode causar um disparo nos casos que é quase tão ruim como se tivessemos feito o Cenário 0: Absolutamente Nada.

**Um lockdown não é a cura, ele é apenas um reinício.**

Então o que? Nós apenas entramos em lockdown de novo e de novo?

###Cenário 3: Lockdown Intermitente

Esta solução foi sugerida inicialmente pelo relatório do Imperial College de 16 de março, e de novo por um artigo de Harvard.[^lockdown_harvard]

[^lockdown_harvard]: "Na falta de outras intervenções, uma métrica chave para o sucesso do distanciamento social é se as capacidades críticas de cuidado são excedidas. Para evitar isto, distanciamento social prolongado ou intermitente pode ser necessário até 2022." [Kissler and Tedijanto et al](https://science.sciencemag.org/content/early/2020/04/14/science.abb5793)

**Aqui está uma simulação:** (Depois de brincar com o "cenário gravado", você pode tentar simular seus *próprios* cronogramas de lockdown, mudando os cursores *enquanto* a simulação está rodando! Lembre-se que você pode parar e continuar a simulação, e alterar a sua velocidade).

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-4&format=lines" width="800" height="540"></iframe>
</div>

Isto *iria* manter os casos abaixo da capacidade das UTIs! E é *muito* melhor que um lockdown de 18 meses até que uma vacina esteja disponível. (E se não houver vacina, repita até que a imunidade de rebanho seja atingida... em 2022.)

Veja, é legal desenhar uma linha dizendo "capacidade das UTIs", mas tem várias coisas importantes que nós *não podemos* simular aqui. Como:

**Saúde Mental:** Solidão é um dos maiores fatores de risco para depressão, ansiedade, e suicídio. E está tão associado com a morte prematura quanto fumar 15 cigarros por dia.[^loneliness]

Veja [Figure 6 from Holt-Lunstad & Smith 2010](https://journals.sagepub.com/doi/abs/10.1177/1745691614568352). Claro, grande ressalva que eles encontraram uma *correlação*. Mas a não ser que você queira tentar aleatóriamente designar pessoas para serem solitárias a vida toda evidência de observação é tudo que você pode ter. 

**Saúde Financeira:** "E a respeito da economia" soa como se você se importasse mais com dólares que com vidas, mas "a economia" não é apenas a bolsa de valores: é a capacidade das pessoas prover comida e abrigo para os seus entes queridos, para investir no futuro dos seus filhos, e desfrutar de artes, comidas, videogames - as coisas que fazem a vida valer a pena. E além disto, pobreza *por si só* tem impactos horríveis na saúde mental e física.

Não estou dizendo que nós *não devamos* ter outro lockdown! Nós iremos falar de lockdowns "disjuntores" depois. De toda forma não é o ideal.

Mas espere... Formosa e a Coréia do Sul não contiveram a COVID-19? Por 4 meses inteiros *sem* quarentenas de longo prazo?

Como?

###Cenário 4: Teste, Rastreie, Isole

*"Claro, nós \*poderíamos\* ter feito o que Formosa e Coréia do Sul fizeram desde o início, mas agora é tarde demais. Nós perdemos a largada."*

Mas é exatamente isto! "Uma quarentena não é a cura, é apenas um recomeço"... **e um recomeço do zero é tudo que precisamos.**

Para entender como Formosa e Coréia do Sul contiveram o COVID-19, nós necessitaríamos entender a exata linha do tempo de uma típica infecção de COVID-19[^timeline]:  

[^timeline]: **3 dias em média para o contágio:** “Assumindo uma distribuição do período de incubação de 5.2 dias, em média, resultado de um estudo em separado dos primeiros casos de COVID-19, nós inferimos que o contágio começa a partir de 2.3 dias ((95% IC, 0.8-3.0 dias) antes dos sintomas se instalarem." (traduzindo: assumindo que os sintomas começam no dia 5, o contágio começa 2 dias antes = contágio começa no dia 3)[He, X., Lau, E.H.Y., Wu, P. et al.](https://www.nature.com/articles/s41591-020-0869-5)
    
	**4 dias na média para infectar outra pessoa:** "The mean [serial] interval was 3.96 dias (95% IC 3.53-4.39 dias)" [Du Z, Xu X, Wu Y, Wang L, Cowling BJ, Ancel Meyers L](https://wwwnc.cdc.gov/eid/article/26/6/20-0357_article)
    
   	**5 dias em média para sentir os sintomas:** "O período médio de incubação foi estimado em 5.1 dias (95% IC, 4.5 a 5.8 dias)" [Lauer SA, Grantz KH, Bi Q, et al](https://annals.org/AIM/FULLARTICLE/2762808/INCUBATION-PERIOD-CORONAVIRUS-DISEASE-2019-COVID-19-FROM-PUBLICLY-REPORTED)

![](pics/timeline1.png)

Se os casos só se auto-isolam quando eles sabem que estão doentes (isto é, eles sentem sintomas), o vírus ainda pode se espalhar:

![](pics/timeline2.png)

E de fato, 44% de todas as transmissões são assim: *pré*-sintomáticas! [^pre_symp]

[^pre_symp]: “Nós estimamos que 44% (95% IC, 25-69%) de casos secundários foram infectados durante o estágio pré-sintomático dos casos índice"[He, X., Lau, E.H.Y., Wu, P. et al](https://www.nature.com/articles/s41591-020-0869-5)

Mas, se nós encontrarmos *e colocarmos em quarentena* os contatos próximos recentes de um caso sintomático... nós paramos o espalhamento, por estar um passo a frente!

![](pics/timeline3.png)

Isto é chamado **rastreamento de contato**. É uma idéia antigaa, que foi utilizada em uma escala sem precedentes para conter o Ebola[^ebola], e agora é parte central de como Formosa e Coréia do Sul estão contendo o COVID-19!

[^ebola]: “Rastreamento de contatos foi uma intervenção crítica na Libéria e representou um dos maiores esforços de rastreamento de contatos durante uma epidemia na história.” [Swanson KC, Altare C, Wesseh CS, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6152989/)

(Isto também permite que utilizemos nossos recursos de teste limitados de forma mais eficiente, para encontrar <icon i></icon>s pré-sintomáticos sem a necessidade de testar quase todo mundo).

Tradicionalmente, os contatos são encontrados com entrevistas pessoais, mas estas *sozinhas* são muito lentas para a janela de ~48h do COVID-19. Este é o motivo pelo qual os rastreadores de contato precisam de ajuda, e serem auxíliados por - *NÃO* substituídos por - apps de rastreamento de contatos.

(Esta idéias não surgiu de "techies": usar um app para lutar contra o COVID-19 foi proposto por [um time de epidemiologistas de Oxford](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936).)

Mas espere aí, apps que rastreiam com quem você esteve em contato?... Isto significa abrir mão da sua privacidade, sucumbindo ao Big Brother?

Nada disto! **[DP-3T](https://github.com/DP-3T/documents#decentralized-privacy-preserving-proximity-tracing)**, um time de epidemiologistas e criptografos (incluindo um de nós, Marcel Salathé) *já* está desenvolvento um app de rastreamento de contatos - com o código disponível para o público - que não revela **nenhuma informação sobre a sua identidade, localização, quem são seus contatos, ou nem mesmo *quantos contatos* você teve.**

Aqui está como ele funciona:

![](pics/dp3t.png)

(& [e aqui está o quadrinho completo](https://ncase.me/contact-tracing/))

Junto com times similares como o protocolo TCN[^tcn] e MIT PACT[^pact], eles inspiraram a Apple e o Google para inserir o rastreamento de contatos, com prioridade na privacidade, diretamente no Android/iOS.[^gapple] (Você não confia no Google/Apple? Ótimo! A beleza deste sistema é que ele não *precisa* de confiança!) Em breve sua agência de saúde pública local pode solicitar que você baixe um app. Se ele colocar privacidade em primeiro lugar, com código-fonte público por favor faça! 

[^tcn]: [TCN - Números de Contato Temporários, um protocolo de rastreamento de contatos descentralizado, com privacidade em primeiro lugar](https://github.com/TCNCoalition/TCN#tcn-protocol)

[^pact]: [PACT: Rastreamento de Contatos Automatizado com Privacidade](https://pact.mit.edu/)

[^gapple]: [Apple e Google fazem parceria em tecnologia de rastreamento de contatos para o COVID-19](https://www.apple.com/ca/newsroom/2020/04/apple-and-google-partner-on-covid-19-contact-tracing-technology/). Repare que *eles mesmos* não estão fazendo os apps, apenas criando os sistemas que darão *suporte* a estes apps.

Mas e as pessoas que não tem smartphones? Ou as infecções por maçanetas de portas? Ou casos "verdadeiramente" assintomáticos? Os apps de rastreamento de contatos não podem pegar todas estas transmissões... *e isto não é problema!* Nós não precisamos pegar *todas* as transmissões, apenas 60%+ para conseguir R < 1.

(Resmungo sobre a confusão a respeito de casos pré-sintomáticos vs "verdadeiramente" assintomáticos. "Verdadeiramente" assintomáticos são raros:[^rant])

[^rant]: Muitos artigos de notícia - e honestamente, muitos artigos científicos - não distinguem entre "casos que não mostraram nenhum sintoma quando nós os testamos" (pré-sintomáticos) e "casos que não mostraram nenhum sintoma *nunca*" (verdadeiramente assintomáticos). A única forma de você diferenciá-los é fazer o acompanhamento dos casos depois.
   
	E isto é o que [este estudo](https://wwwnc.cdc.gov/eid/article/26/8/20-1274_article) fez. (Ressalva: "Artigos com divulgação antecipada não são considerados como versões finais.") Em um call center na Coréia do Sul onde houve um surto "apenas 4 (1.9%) permaneceram assintomáticos dentro de 14 dias de quarentena, e nenhum de seus contatos domiciliares adquiriram infecções secundárias."
    
	Então isto significa que "verdadeiramente assintomáticos" são raros, e ser contaminado por um verdadeiramente assintomático pode ser ainda mais raro!

O isolamento de casos *sintomáticos* reduziria R em cerca de 40%, e colocando em quarentena os seus contatos *pré-sintomáticos ou assintomáticos* reduziria R em até 50%[^oxford]:

[^oxford]: Do mesmo estudo de Oxford que inicialmente recomendou o uso de apps para combater a COVID-19: [Luca Ferretti & Chris Wymant et al](https://science.sciencemag.org/content/early/2020/04/09/science.abb6936/tab-figures-data) Veja a Figura 2. Assumindo R<sub>0</sub> = 2.0, eles encontraram que:    
  
	* Sintomáticos contribuem R = 0.8 (40%)
    * Pré-sintomáticos contribuem R = 0.9 (45%)
    * Assintomáticos contribute R = 0.1 (5%, apesar que o seu modelo tem incertezas e este valor pode ser muito mais baixo)
	* Elementos ambientais como maçanetas contribuem R = 0.2 (10%)

	E adicione os contatos pré & assintomáticos (45% + 5%) e você terá 50% de R!

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-4a&format=calc" width="285" height="340"></iframe>
</div>

Então, mesmo sem 100% de distanciamento, nós podemos chegar a R < 1 *sem um lockdown!* Muito melhor para a nossa saúde mental e financeira. (E para os custos das pessoas que tiverem que se auto-isolar/entrar em quarentena, *os governos devem sustentá-los* - pagar pelos testes, proteger seus empregos, subsidiar licenças remuneradas, etc. Ainda será muito mais barato que lockdown intermitente.)

Se nós mantivermos R < 1 até que nós tenhamos uma vacina, que tornará suscetíveis <icon s></icon>s em imunizados <icon r></icon>s. Imunidade de rebanho, o jeito *certo*:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-4b&format=calc" width="285" height="230"></iframe>
</div>

(Note: this calculator pretends the vaccines are 100% effective. Just remember that in reality, you'd have to compensate by vaccinating *more* than "herd immunity", to *actually* get herd immunity)

Okay, enough talk. Here's a simulation of:

1. A few-month lockdown, until we can...
2. Switch to "Test, Trace, Isolate" until we can...
3. Vaccinate enough people, which means...
4. We win.

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-5&format=lines" width="800" height="540"></iframe>
</div>

So that's it! That's how we make an emergency landing on this plane.

That's how we beat COVID-19.

...

But what if things *still* go wrong? Things have gone horribly wrong already. That's fear, and that's good! Fear gives us energy to create *backup plans*.

The pessimist invents the parachute.

###Scenario 4+: Masks For All, Summer, Circuit Breakers

What if R<sub>0</sub> is way higher than we thought, and the above interventions, even with mild distancing, *still* aren't enough to get R < 1?

Remember, even if we can't get R < 1, reducing R still reduces the "overshoot" in total cases, thus saving lives. But still, R < 1 is the ideal, so here's a few other ways to reduce R:

**Masks For All:**

*"Wait,"* you might ask, *"I thought face masks don't stop you from getting sick?"*

You're right. Masks don't stop you from getting sick[^incoming]... they stop you from getting *others* sick.

[^incoming]: “None of these surgical masks exhibited adequate filter performance and facial fit characteristics to be considered respiratory protection devices.” [Tara Oberg & Lisa M. Brosseau](https://www.sciencedirect.com/science/article/pii/S0196655307007742)

[^outgoing]: “The overall 3.4 fold reduction [70% reduction] in aerosol copy numbers we observed combined with a nearly complete elimination of large droplet spray demonstrated by Johnson et al. suggests that surgical masks worn by infected persons could have a clinically significant impact on transmission.” [Milton DK, Fabian MP, Cowling BJ, Grantham ML, McDevitt JJ](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3591312/)

[^homemade]: [Davies, A., Thompson, K., Giri, K., Kafatos, G., Walker, J., & Bennett, A](https://www.cambridge.org/core/journals/disaster-medicine-and-public-health-preparedness/article/testing-the-efficacy-of-homemade-masks-would-they-protect-in-an-influenza-pandemic/0921A05A69A9419C862FA2F35F819D55) See Table 1: a 100% cotton T-shirt has around 2/3 the filtration efficiency as a surgical mask, for the two bacterial aerosols they tested.

![](pics/masks.png)

Para colocar um número nisto: máscaras cirúrgicas *em uma pessoa doente* reduzem vírus de gripe e resfriado em aerosóis em 70% [^outgoing] Reduzir as transmissões em 70% teria um impacto tão grande quanto um lockdown!

Entretanto, nós não sabemos com certeza o impacto das máscaras *especificamente* no COVID-19. Em ciência alguém só pode publicar uma descoberta se estiver com 95% de certeza. (...poderia.[^replication]) Máscaras, em 1 de maio de 2020, são menos de "95% de certas" de funcionar.

[^replication]: Qualquer cientista de verdade que leu o parágrafo acima está provavelmente morrendo de rir agora. Veja: [p-hacking](https://en.wikipedia.org/wiki/Data_dredging), [the replication crisis](https://en.wikipedia.org/wiki/Replication_crisis))

Entretanto pandemias são como poker. **Aposte apenas quando você tiver 95% de certeza e você perderá tudo que está em jogo.** Como um artigo recente sobre máscaras no British Medical Journal diz [^precautionary] nós *temos* que fazer análises de custo/benefício diante da incerteza. Assim sendo:

[^precautionary]: “É hora de aplicar o princípio da precaução.” [Trisha Greenhalgh et al \[PDF\]](https://www.bmj.com/content/bmj/369/bmj.m1435.full.pdf)

Custos: Se máscaras caseiras de tecido (que tem ~2/3 da efetividade das máscaras cirúrgicas[^homemade]), super baratas. Se máscaras cirúrgicas, mais caro, mas ainda bem barato.

Benefícios: Mesmo se para uma chance de 50-50 de máscaras cirúrgicas reduzirem a transmissão por 0% ou 70%, na média o "valor esperado" é ainda 35%, o mesmo que meio lockdown! Então vamos chutar que máscaras cirúrgicas reduzem R em até 35%, descontada por toda a nossa incerteza. (De novo, você pode desafiar nossas premissas movendo os cursores para cima/para baixo)

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-6a&format=calc" width="285" height="380"></iframe>
</div>

(outros argumentos a favor/contra máscaras:[^mask_args])

[^mask_args]: **"Nós precisamos reservar os insumos para os hospitais."** *Concordo totalmente.* Mas este é mais um argumento para aumentar a produção de máscaras, e não para racionar. No meio tempo nós podemos usar máscaras de pano.

   **"Elas são difíceis de usar corretamente."** Também é difícil de lavar suas mãos de acordo com a recomendações da OMS - sério, "Passo 3) palma da mão direita sobre o dorso da mão esquerda"?! - mas nós ainda podemos recomendar a lavagem de mãos, por que imperfeito ainda é melhor que nada.

   **"Isto fará com que as pessoas se tornem descuidadas com menos lavagens de mãos e distanciamento social."** Claro, e cintos de segurança fazem as pessoas ignorarem sinais de trânsito, e passar fio dental faz com que pessoas comam pedras. Mas sério, nós podemos argumentar o contrário: máscaras são um *lembrete físico constante* para ser cuidadoso - e na Ásia Oriental máscaras são também um símbolo de solidariedade!

*Apenas* as máscaras não tornarão R < 1. Mas se a lavagem de mãos & "Testar, Rastrear e Isolar" só nos levar a R = 1.10, ter apenas 1/3 da população usando máscaras será o suficiente para levar a R < 1, vírus contido!

**Verão:**

Certo, isto não é uma "intervenção" que nós podemos controlar, mas também ajuda! Alguns veículos de notícias reportam que o verão não fara diferença para a COVID-19. Eles estão meio certos: o verão não irá fazer R < 1, mas ele *irá* reduzir R.

Para a COVID-19, cada 1º Celsius a mais faz com que R caia 1.2%. [^heat] A diferença de temperatura verão/inverno na cidade de Nova Iorque é 15ºC, então o verão fará R cair 18%.

[^heat]: “Aumento de 1º Celsius na temperatura [...] diminui R em 0.0225” e “O valor médio de R destas 100 cidades é 1.83”. 0.0225 ÷ 1.83 = ~1.2%. [Wang, Jingyuan and Tang, Ke and Feng, Kai and Lv, Weifeng](https://papers.ssrn.com/sol3/Papers.cfm?abstract_id=3551767)

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-6b&format=calc" width="285" height="220"></iframe>
</div>

Apenas o verão não trará R < 1, mas se temos recursos limitados, nós podemos reduzir a escala de algumas intervenções no verão - para que nós possamos *aumentar* a sua escala no inverno.

**Um Confinamento "Interruptor":**

E se tudo isto *ainda* não for suficiente para fazer R < 1... nós podemos ter outro confinamento.

Mas nós não precisaríamos ficar fechados por 2 meses / abertos por 1 mês para sempre! Por que como R foi diminuído nós só precisaríamos de um ou dois confinamentos "interruptores" antes que uma vacina esteja disponível. (Cingapura teve que fazer isto recentemente, "apesar" de ter controlado a COVID-19 por 4 meses. Isto não é falha: isto *é* o que o sucesso requer.)

Aqui está uma simulação para um cenário "simplificado":

1. Confinamento, e então
2. Uma quantidade moderada de higiene e "Testar, Rastrear, Isolar", com uma pequena quantidade de "Máscaras para Todos", e então.
3. Mais um confinamento "Interruptor" antes que a vacina seja encontrada.

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=int-7&format=lines&height=620" width="800" height="620"></iframe>
</div>

Sem mencionar todas as *outras* intervenções que poderíamos fazer, para empurrar R para baixo:

* Restrições de viagem/quarentenas
* Verificações de Temperatura em centros comerciais e escolas
* Limpeza profunda de espaços públicos
* [Substituir apertos de mão por cumprimento com os pés](https://twitter.com/V_actually/status/1233785527788285953)
* E tudo mais que a engenhosidade humana pode trazer

. . .

Nós esperamos que estes planos dêem esperança para você.

**Mesmo em um cenário pessimista é possível bater o COVID-19, enquanto protegemos nossa saúde mental e financeira.** Usando o lockdown como um "botão de reinício", mantendo R < 1 com isolaamento de casos + rastreamento de contatos que proteja a privacidade + *pelo menos* máscaras de pano para todos... e a vida pode voltar a uma normalidade!

Claro, você pode terá suas mãos ressecadas, mas você poderá convidar alguém para um encontro em uma livraria de histórias em quadrinhos! Você poderá sair com amigos para assistir o último caça-níqueis de Hollywood. Você poderá ficar observando as pessoas em uma livraria, ficando alegre de vê-las fazendo coisas simples como *estarem vivas.*.

Mesmo no cenário de pior caso... a vida persevera.

Então agora vamos planejar para alguns dos *piores* cenários dentre os de pior caso. Aterrisando na água, pegue seu colete de sobrevivência, e por favor siga as luzes para as saídas de emergência:

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>Os Próximos Anos</div>
    </div>
</div>

Se você tiver COVID-19, e se recuperar. Ou tomar a vacina da COVID-19. De qualquer forma você agora estará imune...

...*por quanto tempo?*

* COVID-19 é mais similar ao SARS, que dava aos seus sobreviventes 2 anos de imunidade.[^SARS immunity]
* Os coronavírus que causam "o" resfriado comum dão a você 8 meses de imunidade.[^cold immunity]
* Há relatos de pessoas recuperadas do COVID-19, que depois voltam a testar positivo, mas ainda é incerto se estes são falsos positivos.[^unclear]
* Um estudo *ainda-não-revisado-por-pares* em macacos mostrou imunidade ao coronavírus do COVID-19 por pelo menos 28 dias.[^monkeys]

Mas para o COVID-19 *em humanos*, em 1 de maio de 2020, o "quanto tempo" é a grande dúvida.

[^SARS immunity]: "Anticorpos específicos para o SARS foram mantidos por uma média de 2 anos [...] Então pacientes do SARS devem ser suscetíveis a reinfecção ≥3 anos depois da exposição inicial." [Wu LP, Wang NC, Chang YH, et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2851497/) "Infelizmente" nós nunca saberemos por quanto tempo a imunidade do SARS teria realmente durado já que a erradicamos tão rapidamente.

[^cold immunity]: "Nós não encontramos nenhuma diferença significativa entre a probabilidade de testar positivo pelo menos uma vez e a probabilidade de recorrência para os beta-coronavírus HKU1 e OC43 em 34 semanas depois da inscrição/primeira infecção." [Marta Galanti & Jeffrey Shaman (PDF)](http://www.columbia.edu/~jls106/galanti_shaman_ms_supp.pdf)

[^unclear]: "Uma vez que uma pessoa enfrentou um vírus partículas virais tendem a permanecer por algum tempo. Estas não podem causar infecções, mas elas podem disparar um teste positivo." [de STAT News por Andrew Joseph](https://www.statnews.com/2020/04/20/everything-we-know-about-coronavirus-immunity-and-antibodies-and-plenty-we-still-dont/)

[^monkeys]: De [Bao et al.](https://www.biorxiv.org/content/10.1101/2020.03.13.990226v1.abstract) 
*Ressalva: Este artigo é uma pré-impressão e não foi certificado por revisão por pares (ainda).* Também para enfatizar: eles somente testaram para reinfecção 28 dias depois.

Para estas simulações, digamos é um ano.
**Aqui temos uma simulação iniciando com 100% <icon r></icon>**, decaindo exponencialmente para suscetíveis, sem imunidade <icon s></icon>s depois de 1 ano, na *média*, com variação:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=yrs-1&format=lines&height=600" width="800" height="600"></iframe>
</div>

O Retorno do decaimento exponencial!

Este é o **Modelo SEIRS**. O último "S" significa <icon s></icon> suscetível, de novo.

![](pics/seirs.png)


Agora vamos simular um surto de COVID-19, no período de 10 anos, sem intervenções... *se a imunidade durar apenas um ano:*

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=yrs-2&format=lines&height=600" width="800" height="600"></iframe>
</div>

Nas simulações prévias, nós tinhamos apenas *um* pico de superlotação das UTIs. Agora nós temos vários, *e* <icon i></icon> casos convergem para ficar *permanentemente na* capacidade das UTIs. (Que, lembre-se, nós *triplicamos* para estas simulações)

R = 1, é **endêmico.**

Felizmente, como o verão reduz o R isto melhorará a situação:

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=yrs-3&format=lines&height=640" width="800" height="640"></iframe>
</div>

Oh.

Contraintuitivamente, o verão faz os surtos piores *e* regulares! Isto acontece por que o verão reduz novos <icon i></icon>s, mas isto por outro lado reduz novos <icon r></icon>s imunes. O que significa que a imunidade despenca no verão, *criando* surtos grandes e regulares no inverno.

Por sorte, a solução é bem direta - apenas vacines as pessoas todo outono/inverno, como nós fazemos com as vacinas da gripe:

**(Depois de rodar a simulação padrão tente simular suas próprias campanhas de vacinação! Lembre-se que você pode pausar/continuar a simulação a qualquer momento)**

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=yrs-4&format=lines" width="800" height="540"></iframe>
</div>

Mas aqui vai uma questão mais assustadora:

E se não houver vacina por *anos*? Ou *nunca?*

**Para deixar claro: isto é improvável.** A maior parte dos epidemiologistas espera uma vacina em 1 ou 2 anos. Claro, nunca houve uma vacina para outro coronavírus antes, mas por que a SARS foi erradicada rapidamente, e "a" gripe comum não vale o investimento.

Ainda, pesquisadores de doenças infecciosas expressaram preocupações: E se nós não pudermos fazer a quantidade suficiente?[^vax_enough] E se nós corrermos com ela, e ela não for segura?[^vax_safe]

[^vax_enough]: “Se uma vacina para o coronavírus surgir poderemos fazer em quantidade suficiente?” [por Roxanne Khamsi, na revista Nature](https://www.nature.com/articles/d41586-020-01063-8)

[^vax_safe]: “Não corra para distribuir vacinas e drogas para o COVID-19 sem garantias de segurança suficientes"[por Shibo Jiang, na revista Nature](https://www.nature.com/articles/d41586-020-00751-9)

Mesmo no cenário de pesadelo de "sem vacinas", nós ainda temos 3 saídas. Da mais para a menos terrível:

1) Fazer intervenções R < 1, intermitentes ou avulsas, para atingir a "imunidade de rebanho natural". (Aviso: isto resultará em muitas mortes e pulmões lesionados). *E* não irá funcionar se a imunidade não durar.)

2) Fazer intervenções R < 1 para sempre. Rastreamento de contatos e usar máscaras simplesmente se tornará a nova norma no mundo pós-COVID-19, como testes para DST e usar camisinhas se tornaram a nova norma no mundo pós-HIV.

3) Fazer intervenções R < 1 até que nós desenvolvamos tratamentos que façam a COVID-19 muito, muito menos provável de precisar de cuidados intensivos. (O que nós devemos já estar fazendo *de qualquer forma!*) Reduzindo o uso de UTIs por um fator de 10x é o mesmo que aumentar nossa capacidade de leitos de UTI em 10x:

**Aqui está uma simulação de imunidade *não* duradoura, *sem* vacinas, e mesmo sem nenhuma intervenção - apenas incrementando lentamente a capacidade de sobrevivência aos surtos de longo prazo:**

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=yrs-5&format=lines" width="800" height="540"></iframe>
</div>

Até mesmo sob o cenário de *pior* caso... a vida persevera.

. . .

Talvez você goste de desafiar nossas premissas, e tentar R<sub>0</sub>'s ou números diferentes. Ou tentar simular suas *próprias* combinações de planos de intervenção!

**Aqui está um Modo de Caixa de Areia(optional), com *tudo* disponível. (role a tela para ver todos os controles) Simule e brinque a vontade:**

<div class="sim">
		<iframe src="https://ncase.github.io/covid-19/sim?stage=SB&format=sb" width="800" height="540"></iframe>
</div>

Este "simulador de vôo epidemico" básico nos ensinou tanto. Ele nos permite responder questões sobre nossos últimos meses, os próximos meses, e os próximos anos.

Então finalmente, vamos retornar para...

<div class="section chapter">
    <div>
		<img src="banners/curve.png" height=480 style="position: absolute;"/>
        <div>O Agora</div>
    </div>
</div>

O avião afundou. Nós subimos nos botes salva-vidas. É hora de encontrar terra firme.[^dry_land]

[^dry_land]: A metáfora de terra firme [de Marc Lipsitch & Yonatan Grad, em STAT News](https://www.statnews.com/2020/04/01/navigating-covid-19-pandemic/)


Equipes de epidemiologistas e governantes ([left](https://www.americanprogress.org/issues/healthcare/news/2020/04/03/482613/national-state-plan-end-coronavirus-crisis/), [right](https://www.aei.org/research-products/report/national-coronavirus-response-a-road-map-to-reopening/ ), e [multi-partisan](https://ethics.harvard.edu/covid-roadmap)) chegaram a um consenso em como bater a COVID-19, enquento protegem nossas vidas *e* liberdades. 

Aqui segue uma idéia geral, com alguns (menos consensuais) planos de emergência:

![](pics/plan.png)

Então o que isto significa para VOCÊ, agora?

**Para todo mundo** Respeite a quarentena para que nós possamos sair da Fase I tão logo quanto possível. Continue lavando as suas mãos. Faça suaa própria máscara. Baixe um app de rastreamento de contatos *que protejam identidades* quando estes estiverem disponíveis no próximo mês. Se mantenha física e mentalmente saudável! E escreva para seu legislador local para levantar a bunda da cadeira e...

**Para legisladores:** Crie leis que deem suporte a quem tem que se isolar/ficar em quarentena. Contrate mais rastreadores de contato manuais, *auxiliados* por app de rastreamento de contatos *que protejam identidades*. Direcione mais fundos para as coisas que deveríamos estar fazendo, tais como...

**Para produtores:** Produzam testes. Produzam respiradores. Produzam equipamentos de proteção para hospitais. Produzam testes. Produzam máscaras. Produzam apps. Produzam antivirais, profiláticos, e outros tratamentos que não são vacinas. Produzam vacinas. Produzam testes. Produzam testes. Produzam testes. Produzam esperança.

Não minimize o medo para construir esperança. Nosso medo deve *trabalhar junto* com nossa esperança, como os inventores de aviões e paraquedas. Se preparar para futuros horríveis é como nós *criamos* um futuro de esperança.

A única coisa a temer é a idéia que a única coisa a temer é o próprio medo.
