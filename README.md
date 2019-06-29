# Git - Anotações de uso.

**_O que é?_**

É uma ferramenta de versionamento de código ou controle de versão, é usado para se manter um histórico de todas as alterações que foram realizadas no projeto, assim sendo mais fácil caso seja necessario visualizar um determinado ponto e voltar a ele. E com essa ferramenta é possível trabalhar com mais de um desenvolvedor em um projeto, alterando o mesmo código ou até a mesma linha, sem ter que utilizar algum
software de comparação ou esperar que outro programador termine sua modificação, antes de fazer a sua implementação.

**_Começando a versionar_**
* Baixe e instale o [GIT](https://git-scm.com/)
* Baixe e instale o terminal [cmder](https://cmder.net/)

* Após a instalação de ambos os itens, abra o terminal (cmder) e rode o seguinte comando:

```
git --version
```
> Com esse comando será retornado a versão do git e assim é possivel ter certeza que o git foi instalado corretamente.

* Agora que o git está instalado é necessario criar uma configuração global com seu nome e email, dessa forma todas as mudanças de código que forem feitas, já receberam a sua assinatura, assim sendo possível aos outros desenvolvedores, saberem quem fez aquele código. Para isso rode o seguinte comando:

```
git config –global user.name "Nome de usuario do GitHub"
git config –global user.email "Email cadastrado no GitHub"
```

* **_Entrando em uma determinada pasta pelo terminal_**

```
cd [NomeDoDiretorio/Pasta]  --> Entra no diretorio referido.
ex: cd desktop/workspace

ls                          --> Mostra os arquivos no diretorio.

cd ..                       -->Volta um diretorio.

clear                       -->Limpa o terminal
```

> A tecla TAB pode ajudar na hora de digitar o nome do diretorio pois ele alto-completa a digitação.

* **_Criando um repositorio:_**

```
git init --> Transforma a pasta onde o terminal se localiza em um repositorio assim acompanhando o versionamento daquele diretorio.

git status --> Retorna o status atual do repositorio, mostrando se é necessário commitar tal trabalho.
```

* **_Após ter criado o repositorio._**

Tudo que se tem que fazer agora é adicionar os arquivos da aplicação, na pasta do projeto, seguido dessa adição podemos rodar o comando **git status** e perceper que é retornado a seguinte mensagem:

> Você tem arquivos que não estão sendo trackados pelo git, os arquivos em questão são: (nomes em vermelho)

_Track: Acompanhamento do controle de versão_

Juntamente com a mensagem o git notifica que é melhor dar um **git add** para ele começar a acompanhar esses arquivos.

* E é isso que se deve fazer, após terminar de adicionar e editar os arquivos base do seu projeto, rodamos o  seguinte comando para que o git possa fazer o acompanhamento:

```
git add [NomeDoArquivo.Extenção]  --> Acompanha o arquivo referido.

git add .[extenção]               --> Será acompanhado todos os arquivos com essa extenção.

git add .                         --> Será acompanhado todos os arquivos do diretorio 
```

* **_Commitando_**

Após dado o comando **git add** se for checado os status será retornado que há alterações para serem comitadas.

> Quando se faz a utilização do _git add_ fazemos os arquivos sairem do "Work Directory" e irem para uma especie de sala de espera a "Stage Area", antes de serem mandados para o historico. Ou seja o _commit_  nada mais é do que a marcação de um ponto na historia do projeto. Similar ao ponto de restauração do windows.

O comando para commitarmos é:

```
git commit -m "Mensagem breve sobre o trabalho realizado"
```
Se for checado o status de novo sera retornado que não há alterações pendentes de salvamento.

* **_Cituações para ignorar_**

Digamos que você esteja trabalhando em projeto e nele você adiciona documentos de notificação, pacotes pelo npm ou de modo geral algo que não se quer que o git faça o controle de suas versões. Para que seja possivel fazer com que o git ignore determinado arquivo  precisamos apenas:

--Crie dentro da pasta do projeto, um arquivo denominado de **.gitignore**, e dentro deste arquivo coloque o nome do arquivo ou pasta que se deseja ser ignorada.

* **_RECAPITULANDO_**

Começou a trabalhar no projeto, editou todos os arquivos e tal, abra o **cmder** vá ate a pasta do projeto e verifique o estatus caso queira com **git status**,  neste caso o estatus dirá que se tem mudanças pendentes, então faremos um **git add .**, e após isso faremos um **git commit –m “mensagem”** salvando assim as alterações.

* **_Pulando Passos sem errar_**

Com o comando:
```
git commit -a -m "Mensagem"
```

Fará com que o comando **Add** não precise ser dado, pois fará isso automaticamente, porem o arquivo não irá para a _stage área_ o que significa que ele terá um salvamento direto. Porém é aconselhável deixar os arquivos na _stage área_ pois assim é possível reverter diferentes tipos de alterações ou seja remover determinado arquivo que não se queria na _stage_

* **_Sabendo o que foi alterado na edição**_

Para consultar todas as alterações feitas em um arquivo que está em seu diretório de trabalho mas que ainda não foi adicionado para a stage se pode utilizar o seguinte comando:

```
git diff --> Ele retorna os arquivos que foram modificados e as linhas que foram adicionadas ou apagadas.
```

Tendo colocado os documentos na stage o git diff não será capas de mostrar as mudanças feitas , mas para contornar isso e verificar as mudanças dos doc’s mesmo esse estando na stage , usamos o comando:

```
git diff --staged
```  

Para podermos ver os coommit’s dados no projeto desde o início fazemos o seguinte comando:

```
git log  Ele retorna um histórico de todos os commit’s 
```  

Neste histórico teremos uma espécie de “chave” a chamada **HASH** que serve para referenciar esses commit’s caso se queira voltar a uma versão especifica do projeto.
Caso ache o que o **log** seja um pouco vago e queira saber mais do que foi alterado em cada commit podemos usar alguns parâmetros adicionais:

```
git log –p --> Além de colocar todos os commit’s em ordem cronológica, ele mostrará o diff de cada um dos commit‘s
```  

> Pressionando enter após o comando ele continuará apresentando o log e no final (END) para terminar tem que se pressionar a tecla “Q”.
Porem Temos alguns problemas com esse log dependendo do tamanho do histórico do projeto. Para resolver isso trazendo apenas o que queremos é possível limitar a quantidade de commit’s que serão postos na tela com o log.

```
git log –p –n --> Sendo n o número de entradas que queremos trazer.
```  

* **_Relatório detalhado_**

Ficar vendo linha por linha no terminal pode ser muito improdutivo por isso temos o comando:

```
gitk
```  

> Com esse comando será aberto uma interface gráfica, que mostra todas as alterações desde o commit inicial. E clicando neste commit será mostrado as alterações que foram feitas.

* **_Desfazendo e revertendo alterações_**

Para editar o ultimo commit feito, fazemos as alterações necessárias em segida adicionamos os arquivos alterados na stage área e ao fazer o commit usamos o comando:

```
Git commit –amend –m “Nova Funcionalidade (edição)”
```

Caso Seja feito a adição de um arquivo que não se quer na stage área podemos remove-lo com o seguinte comando:

```
Git reset HEAD [nome e extensão do arquivo]
```

Um outro caso é quando pegamos um projeto de outra pessoa e fazemos grandes alterações. E para revertermos esse arquivo ao formato original ou commitarmos as informações que alteramos.

Para discartarmos as mudanças feitas usamos o comando:

```
Git checkout --[nome do arquivo]
Ex: git checkout –texto.txt
```

E assim o proprio arquivo vai voltar ao estado original.
Caso seja feita a remoção de algum arquivo o git notificará de que há algumas coisasa serem deletadas antes de seguir.

Para apagar os arquivos já apagados do repositório e fazer o git deixar de acompanhar-los temos o seguinte comando:

```
Git rm [nome do arquivo]
``` 

* Tag e Branch

Uma **tag** é uma etiqueta, um ponto de atalho para um determinado status do sistema, geralmente os desenvolvedores utilizam as **tag** para criar marcações nas versões diferentes de m sistema (ex: V1.0...) assim facilitando a troca de status ou seja uma data e hora especifica:
Para listar as tag no sistema (as já criadas)
```
Git tag
```
Para criar uma tag
```
Git tag –a [nome da tag] –m “mensagem” O “–a “ serve para marcar quem criou a tag juntamente com a data e a hora.
```

A Tag é sempre criada no commit atual (Local onde o desenvolvedor está trabalhando)

Criando ua tag com um commit antigo

Primeiro teremos que ver todos os commit’s do nosso sistema feio até o momento:
```
Git log --pretty=oneline
```
Com esse comando será retornado a chave de cada commit, e para referenciar a tag a esse determinado commit segue o seguinte comando:

```
Git tag –a [nome da tag] [chave do commit] –m “mensagem”
```





