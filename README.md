<div align="center">
  <h1><strong>Calendários</strong></h1>
</div>

 *No projeto realizado, o objetivo era realizar uma automatização através de um arquivo.bat para realizar a tarefa de criar um ano e, dentro desse ano, colocar os 12 meses e dentro desses meses a quantidade de dia especifico de cada um através de parâmetros, após isso fazer com que seja indentificado se o mes é bissexto ou não, de tal forma que se for bissexto ele modifique o dia do mes de fevereiro.*

<div align="center">
  <h1><strong>Código</strong></h1>
</div>

<div align="center">
  <img src="https://github.com/user-attachments/assets/43facf68-8aa1-4b1a-ad34-ff7a841642da">
</div>

# Partes principais

```
if %2 gtr 12 (
    echo Mes invalido O mes deve ser entre 1 e 12
    exit /b
)
```
<br>

> Inicialmente no código é feito uma regra para que se for inserido um numero maior que 12 **(quantidade de meses do ano)** ele exiba uma mensagem dizendo que não existe para que prenda os valores entre a quantidade de meses.

<br>

```
set /a "resto=%1 %% 4"
set /a "resto100=%1 %% 100"
set /a "resto400=%1 %% 400"
set /a "conta = %1+4"

if %resto%==0 (
    if %resto100%==0 (
        if %resto400%==0 (
            set dias_fevereiro=29
            echo o proximo ano bissexto e %conta%
        ) else (
            set dias_fevereiro=28
        )
    ) else (
        set dias_fevereiro=29
        echo o proximo ano bissexto e %conta%
    )
) else (
    set dias_fevereiro=28
)
```
<br>

> Parte em que é pego o mes em que foi inserido pelo usuario que esta realizando o processo e fazendo as contas necessárias para ser indentificado se o ano é bissexto ou não, dividindo por 4, por 100 e 400, após isso vendo se teve alguma sobra de divisão **(resto)**. O set foi usado como principal para que fosse mudado a quantidade de dias de fevereiro para 28 ou 29 caso bissexto.

<br>

```
if "%2" == "1" set dias=31
if "%2" == "2" set dias=%dias_fevereiro%
if "%2" == "3" set dias=31
if "%2" == "4" set dias=30
if "%2" == "5" set dias=31
if "%2" == "6" set dias=30
if "%2" == "7" set dias=31
if "%2" == "8" set dias=31
if "%2" == "9" set dias=30
if "%2" == "10" set dias=31
if "%2" == "11" set dias=30
if "%2" == "12" set dias=31

echo O mes %2 tem %dias% dias

for /l %%i in (1,1,%dias%) do (
    if exist %dias% (
        mkdir %%i
    )
)
```
<br>

> Aqui foi criado as variaveis que possuem a quantidade de dias de tal mes dentro do segundo parâmetro, para que fosse possivel a criação deles dentro da pasta com o **For (loop)** e dentro do parenteses adicionando a regra de criar desde o numero 1 (primeiro dia) até a variavel dia selecionada.

<br>

---
# Execução do código

<div align="center">
  <img src="https://github.com/user-attachments/assets/168e40d7-df74-414b-951f-6c577c85c35e">
</div>

<div align="center">
  <h1><strong>Meu aprendizado</strong></h1>
</div>

### Neste projeto aprendi configurar parâmetros que servem para inserir o que eu quero dentro, como neste trabalho inseri dentro do primeiro parâmetro uma função para criar um diretório e após isso inseri outro diretório dentro do outro parâmetro. Aprendi também a caucular divisão e restos da razão dentro da programação .bat.

<br>

# Melhorias
A programação poderia ser mais rueduzida, talvez achando funções eficientes mas menores.
