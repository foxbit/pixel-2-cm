
Meus comentários... rs

## 1. Sobre os cálculos de validação
Eu acho que usar uma múltiplicação pra validar as dimensões não é uma boa ideia.
Por que existem várias combinações que geram o mesmo resultado. Por exemplo:
```javascript
1920 * 1080 = 2073600
2073600 * 1 = 2073600
```

Meu conselho é você trabalhar com as dimensões de forma separada e validá-las de
forma separada também.

Uma opção é você usar valores fixos no codigo fonte (conhecidos como hardcoded).
Por exemplo:
```javascript
let fullscreenWidth = 1920;
let fullscreenHeight = 1080;
...
if (qtdPixelLargura <= fullscreenWidth && qtdPixelAltura <= fullscreenHeight) {
  // Compatível com fullscreen
} else {
  // Não compatível com fullscreen
}
```
Outra opção é usar ```Array```. Que é a forma como eu faria :)

## 2. Sobre as cores dos elementos
Você repetiu valores (as cores) que precisam estar em sincronia em vários pontos diferentes
do código-fonte. Sempre que você mudar um, tem que lembrar de mudar os outros. Num código com 
50 linhas, OK. Mas imagina isso num projeto com 500 arquivos!!!!

Você tem 2 opções:
- a. Criar duas constantes para armazenar os codigos das cores
```javascript
const successColor = '#59CFFB';
const failureColor = '#FF6B66';
...
divResultadoFullScreen.style.background = successColor;
```

- b. (recomendado) Ficaria melhor se você criasse classes CSS com os estilos que representam um formato compatível
e incompatível. Assim, você já criaria o elemento DOM com essa classe - eliminando a necessidade
de definir a cor manualmente para cada elemento. Assim, o trecho
```javascript
divResultadoFullScreen.innerHTML = `Compatível com <strong>HD FullScreen</strong> <i class="fa fa-check-circle"></i>`;
divResultadoFullScreen.style.background = '#59CFFB';
```
ficaria
```javascript
divResultadoFullScreen.innerHTML = `<div class="compatible">Compatível com <strong>HD FullScreen</strong> <i class="fa fa-check-circle"></i></div>`;
```
bastando apenas criar o respectivo CSS
```css
.compatible { background-color: '#59CFFB' }
.incompatible { background-color: '#FF6B66' }
```

## 3. Ponto-e-vírgula
Apesar do JS não obrigar o ponto-e-virgula no fim de cada instrução, é uma boa prática
lembrar de colocá-lo.

Por exemplo, o trecho
```javascript
let fatorFullscreen = 1920 * 1080
let fatorA5 = 1748 * 2480
let fatorA4 = 2480 * 3508
let fatorA3 = 3508 * 4960
let fatorA2 = 4960 * 7016
```

ficaria
```javascript
let fatorFullscreen = 1920 * 1080;
let fatorA5 = 1748 * 2480;
let fatorA4 = 2480 * 3508;
let fatorA3 = 3508 * 4960;
let fatorA2 = 4960 * 7016;
```

## 4. Considerações finais
Programação é isso: resolução de problemas.

Não existe **a melhor** linguagem de programação, existe aquela que a gente sabe trabalhar com 
mais desenvoltura e que está dentro do contexto do problema que queremos resolver (usar C++ para
criar página web não faz sentido.... kkkk).

O primeiro passo é conseguir criar um código que resolva o problema. O segundo passo é torná-lo
mais otimizado (com menos linhas de código, menos processamento, menos memória, etc). Que é o que
chamamos de **refatoração**.

Otimizar um código-fonte não é tarefa fácil e exige apenas uma coisa: conhecimento avançado do
problema e da linguagem.

Quero deixar meus parabéns, por você já ter conseguido resolver um problema real com tão pouca
coisa que você aprendeu até agora
```javascript
 _____                _                    _ 
 |  __ \              | |                  | |
 | |__) |_ _ _ __ __ _| |__   ___ _ __  ___| |
 |  ___/ _` | '__/ _` | '_ \ / _ \ '_ \/ __| |
 | |  | (_| | | | (_| | |_) |  __/ | | \__ \_|
 |_|   \__,_|_|  \__,_|_.__/ \___|_| |_|___(_)
```
