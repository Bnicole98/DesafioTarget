# DesafioTarget

Desenvolvimento de exercícios de lógica de programação.
Técnica:

1.  Observe o trecho de código abaixo:
    int INDICE = 13;
    SOMA = 0, K = 0;
    Enquanto K < INDICE faça {
    K = K + 1;
    SOMA = SOMA + K;
    }
    Imprimir(SOMA);
    Ao final do processamento, qual será o valor da variável SOMA?
    R: 91

        K(0) -> 0 + 1 = 1
        K(1) -> 1 + 2 = 3
        K(2) -> 3 + 3 = 6
        K(3) -> 6 + 4 = 10
        K(4) -> 10 + 5 = 15
        K(5) -> 15 + 6 = 21
        K(6) -> 21 + 7 = 28
        K(7) -> 28 + 8 = 36
        K(8) -> 36 + 9 = 45
        K(9) -> 45 + 10 = 55
        K(10) -> 55 + 11 = 66
        K(11) -> 66 + 12 = 78
        K(12) -> 78 + 13 = 91

/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////

2.  Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência. IMPORTANTE: Esse número pode ser informado através de qualquer entrada de sua preferência ou pode ser previamente definido no código;

        function fibonacciRecursivo(n){
            if(n<=1) return n;
            return fibonacciRecursivo(n-1) + fibonacciRecursivo(n-2);
        }

        function geraSequenciaFibb(n){
            const sequence = [];
            var ultimo = null ;
            var i = 0;
            while(ultimo===null || ultimo<=n){
                sequence.push(fibonacciRecursivo(i));
                ultimo = sequence[i];
                i++;
            }
            return sequence;
        }

        function numeroDentroDaSeq(n){
            const list = geraSequenciaFibb(n);
            console.log("Entrada:"+n);
            console.log("Lista:\n");
            console.log(list);
            if(list.includes(n)){
                console.log("Pertence");
            }else{
                console.log("Não Pertence");
            }
        }

        numeroDentroDaSeq(55);

/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////

3. Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:  
   • O menor valor de faturamento ocorrido em um dia do mês;
   • O maior valor de faturamento ocorrido em um dia do mês;
   • Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;

            const faturamento = [
            {"dia": 1,"valor": 22174.1664},
            {"dia": 2,"valor": 24537.6698},
            {"dia": 3,"valor": 26139.6134},
            {"dia": 4,"valor": 0.0},
            {"dia": 5,"valor": 0.0},
            {"dia": 6,"valor": 26742.6612},
            {"dia": 7,"valor": 0.0},
            {"dia": 8,"valor": 42889.2258},
            {"dia": 9,"valor": 46251.174},
            {"dia": 10,"valor": 11191.4722},
            {"dia": 11,"valor": 0.0},
            {"dia": 12,"valor": 0.0},
            {"dia": 13,"valor": 3847.4823},
            {"dia": 14,"valor": 373.7838},
            {"dia": 15,"valor": 2659.7563},
            {"dia": 16,"valor": 48924.2448},
            {"dia": 17,"valor": 18419.2614},
            {"dia": 18,"valor": 0.0},
            {"dia": 19,"valor": 0.0},
            {"dia": 20,"valor": 35240.1826},
            {"dia": 21,"valor": 43829.1667},
            {"dia": 22,"valor": 18235.6852},
            {"dia": 23,"valor": 4355.0662},
            {"dia": 24,"valor": 13327.1025},
            {"dia": 25,"valor": 0.0},
            {"dia": 26,"valor": 0.0},
            {"dia": 27,"valor": 25681.8318},
            {"dia": 28,"valor": 1718.1221},
            {"dia": 29,"valor": 13220.495},
            {"dia": 30,"valor": 8414.61}
            ]

            function imprimeLista(lista){
            var i = 0;
            for(i = 0; i<lista.length; i++){
            console.log("Dia: " + lista[i].dia+" | valor: " + lista[i].valor);
            }
            }

            function faturamentoDiasUteis(lista){
            var i = 0;
            const faturamentoDiaUtil = [];

                for(i = 0; i<lista.length; i++){
                    if(lista[i].valor > 0){
                        faturamentoDiaUtil.push(lista[i]);
                    }
                }
                return faturamentoDiaUtil;

            }

            function menorFaturamentoMes(lista){
            var i = 0;
            var menorDiaFaturado = null;

                for(i = 0; i<lista.length; i++){
                    if(menorDiaFaturado === null || menorDiaFaturado.valor>lista[i].valor){
                        menorDiaFaturado = lista[i];
                    }
                }
                return menorDiaFaturado;

            }

            function maiorFaturamentoMes(lista){
            var i = 0;
            var maiorDiaFaturado = null;

                for(i = 0; i<lista.length; i++){
                    if(maiorDiaFaturado === null || maiorDiaFaturado.valor<lista[i].valor){
                        maiorDiaFaturado = lista[i];
                    }
                }
                return maiorDiaFaturado;

            }

            function mediaFaturamentoMes(lista){
            var i = 0;
            var mediaFaturamento = 0;

                for(i = 0; i<lista.length; i++){
                    mediaFaturamento = mediaFaturamento + lista[i].valor;
                }
                mediaFaturamento = mediaFaturamento / lista.length;

                return mediaFaturamento;

            }

            function diasSuperiorMedia(lista){
            var i = 0;
            const listaDias = [];
            const mediaFaturamento = mediaFaturamentoMes(lista);

                for(i = 0; i<lista.length; i++){
                    if(lista[i].valor > mediaFaturamento){
                        listaDias.push(lista[i]);
                    }
                }
                return listaDias;

            }

            const listaDiaUtil = faturamentoDiasUteis(faturamento);

            imprimeLista(listaDiaUtil);

            console.log(menorFaturamentoMes(listaDiaUtil));
            console.log(maiorFaturamentoMes(listaDiaUtil));
            console.log(mediaFaturamentoMes(listaDiaUtil));

            console.log("\n\n");

            imprimeLista(diasSuperiorMedia(listaDiaUtil));

/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////

4.  Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:

    • SP – R$67.836,43
    • RJ – R$36.678,66
    • MG – R$29.229,88
    • ES – R$27.165,48
    • Outros – R$19.849,53

    Escreva um programa na linguagem que desejar onde calcule o percentual de representação que cada estado teve dentro do valor total mensal da distribuidora.

         const faturamento = [
             {"estado": "SP","valor": 67836.43},
             {"estado": "RJ","valor": 36678.66},
             {"estado": "MG","valor": 29229.88},
             {"estado": "ES","valor": 27165.48},
             {"estado": "Outros","valor": 19849.53}

         ]

         function somatorioTotal(lista){
             var i = 0;
             var soma = 0;

             for(i = 0; i<lista.length; i++){
                 soma = soma + lista[i].valor;
             }
             return soma;
         }


         function porcetagemEstado(lista){

             const total = somatorioTotal(lista);

             var i =0;
             for(i = 0; i < lista.length; i++){
                 console.log("estado : " + lista[i].estado + "\t\t\t\t|| valor : " + lista[i].valor+ "\t|| % :"+(100*(lista[i].valor / total)));
             }
         }

         porcetagemEstado(faturamento);

/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////
/////////////////////////////////////////////////////////////////////////////////////////////

5.  Escreva um programa que inverta os caracteres de um string.
    IMPORTANTE:
    a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;
    b) Evite usar funções prontas, como, por exemplo, reverse;

             function inverte(palavra){

                 var invertida = "";


                 for (i = palavra.length - 1; i >= 0; i--) {
                 invertida += palavra[i];
                 }
                 return invertida;
             }

             const original = ""


             console.log("String original: " + original);
             console.log("String invertida: " + inverte(original));
