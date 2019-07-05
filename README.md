# Git - Anotações de uso.

**_O que é?_**

É uma ferramenta de versionamento de código ou controle de versão, é usado para se manter um histórico de todas as alterações que foram realizadas no projeto, assim sendo mais fácil caso seja necessario visualizar um determinado ponto e voltar a ele. E com essa ferramenta é possível trabalhar com mais de um desenvolvedor em um projeto, alterando o mesmo código ou até a mesma linha, sem ter que utilizar algum
software de comparação ou esperar que outro programador termine sua modificação, antes de fazer a sua implementação.

### Começando a versionar
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

### Entrando em uma determinada pasta pelo terminal

```
cd [NomeDoDiretorio/Pasta]  --> Entra no diretorio referido.
ex: cd desktop/workspace

ls                          --> Mostra os arquivos no diretorio.

cd ..                       -->Volta um diretorio.

clear                       -->Limpa o terminal
```

> A tecla TAB pode ajudar na hora de digitar o nome do diretorio pois ele alto-completa a digitação.

### Criando um repositorio:

```
git init --> Transforma a pasta onde o terminal se localiza em um repositorio assim acompanhando o versionamento daquele diretorio.

git status --> Retorna o status atual do repositorio, mostrando se é necessário commitar tal trabalho.
```

### Após ter criado o repositorio.

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

### Commitando

Após dado o comando **git add** se for checado os status será retornado que há alterações para serem comitadas.

> Quando se faz a utilização do _git add_ fazemos os arquivos sairem do "Work Directory" e irem para uma especie de sala de espera a "Stage Area", antes de serem mandados para o historico. Ou seja o _commit_  nada mais é do que a marcação de um ponto na historia do projeto. Similar ao ponto de restauração do windows.

O comando para commitarmos é:

```
git commit -m "Mensagem breve sobre o trabalho realizado"
```
Se for checado o status de novo sera retornado que não há alterações pendentes de salvamento.

### Cituações para ignorar

Digamos que você esteja trabalhando em projeto e nele você adiciona documentos de notificação, pacotes pelo npm ou de modo geral algo que não se quer que o git faça o controle de suas versões. Para que seja possivel fazer com que o git ignore determinado arquivo  precisamos apenas:

> Crie dentro da pasta do projeto, um arquivo denominado de **.gitignore**, e dentro deste arquivo coloque o nome do arquivo ou pasta que se deseja ser ignorada.

### RECAPITULANDO

Começou a trabalhar no projeto, editou todos os arquivos e tal, abra o **cmder** vá ate a pasta do projeto e verifique o estatus caso queira com **git status**,  neste caso o estatus dirá que se tem mudanças pendentes, então faremos um **git add .**, e após isso faremos um **git commit –m “mensagem”** salvando assim as alterações.

### Pulando Passos sem errar

Com o comando:
```
git commit -a -m "Mensagem"
```

Fará com que o comando **Add** não precise ser dado, pois fará isso automaticamente, porem o arquivo não irá para a _stage área_ o que significa que ele terá um salvamento direto. Porém é aconselhável deixar os arquivos na _stage área_ pois assim é possível reverter diferentes tipos de alterações ou seja remover determinado arquivo que não se queria na _stage_

### Sabendo o que foi alterado na edição

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
git log --> Ele retorna um histórico de todos os commit’s 
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

### Relatório detalhado

Ficar vendo linha por linha no terminal pode ser muito improdutivo por isso temos o comando:

```
gitk
```  

> Com esse comando será aberto uma interface gráfica, que mostra todas as alterações desde o commit inicial. E clicando neste commit será mostrado as alterações que foram feitas.

### Desfazendo e revertendo alterações

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

### Tag e Branch

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

Se o programador quiser saber mais sobre uma:
git show [Tag]

### Como usar uma tag

Com a tag criada e referenciada é possível visualizar os arquivos que foram commitados na tag referida.
```
Git checkout v0.0
```
> *ao invés de v0.0 podemos usar o “master” para podermos voltar ao branch principal e o inverso se faz da mesma forma ao querermos sair do master para o v0.0.
> *v0.0 é o nome da tag que foi criada para fazer referência ao primeiro commit do projeto.
E assim será feito a troca dos arquivos para aquela versão.
(Exemplo do desenho)

### Como deletar uma tag
```
Git tag –d [Nome da tag]
```
>As tag’s podem não ser uma boa escolha de usabilidade e por isso é recomendado usar branch’s.

### Branch
O branch pode ser comparado em sentido figurado a ramificação dos galhos de uma arvore e com eles é permitido que o user trabalhe com várias ramificações, com várias segmentações de seu sistema fazendo commits que não alteram as outras ramificações.

Para criarmos um branch fazemos da seguinte forma:

```
Git branch test
```
> ”test” é nome do ramo que queremos criar
Depois de criado o ramo se deve fazer a transição dos arquivos trabalhados com o comando:
```
Git checkout test
```
> checkout - -> retorna que foi trocado de ramo.
Quando se sentir mas a vontade podemos usar um comando mais direto:
```
Git checkout –b test
```  
> No caso será criado o branch fazendo já a transferência dos arquivos
Feito isso já é possivel trabalhar no ambiente normalmente. Ao “termino” do trabalho, é feito um commit e se for de preferência, voltamos ao branch master
```
Git checkout master
``` 
A partir do momento que realmente for concluído o trabalho presente no branch criado precisamos (apenas caso queira ou precise) implantar aquele código no máster ou seja no projeto principal e para isso:
-_Teremos que entrar no branch máster._
-_E em seguida fazer o merge_

```
Git merge [nome do branch que se quer pegar as mudanças]
```
>”merge” Pode ser traduzido para juntar/mesclar
>*Algo importante a salientar é que o sistema (a localização do user) sempre terá que estar no branch que é o destino das suas alterações (no caso a origem é o teste de onde as mudanças virão e o máster é o destino que essas mudanças se adaptarão)*

**_Caso esteja usando um editor de texto como o vscode, ao fazer o merge o editor lhe auxiliará sobre quais as mudanças feitas e possíveis correção de código por conta da sobreposição de escrita, isso tudo com apenas alguns cliques_**

Caso não queira mais utilizar determinado branch podemos deletado com o comando:
```
Git branch –d [nome do branch]
```
E se caso se esqueça quais foram os branch’s criados podemos usar o seguinte comando para ver os existentes:
```
Git branch
```

### Os conflitos de merge

Isso acontece quando se tem alterações das mesmas linhas de código feito ou não por mais de um programador. Ao tentar fazer o merge o git retornará uma mensagem informando que o merge automático foi cancelado por esse motivo e que para prosseguir o user terá que corrigir os conflitos na “raça” (mas como já foi comentado o vscode pode ajudar muito nesse quesito). O git dará um auxilio mostrando as linha que se situam os conflitos dando a opção de continuar com um dos códigos. Assim que se corrigir os conflitos terá que ser feito o commit para concluir o merge.

### Git e Rede Local

Com o GitHub podemos ajudar outros desenvolvedores em seus projetos.
Ao fazer o clone dos arquivos, edita-los, e finalizar o trabalho mesmo commitando eles os arquivos não vão necessariamente direto para o repositório de origem, eles ficam na sua máquina local, e para fazer com que este trabalho seja enviado para seu repositório de origem temos o seguinte comando a executarmos:
* Para fazer isso daremos um “push” e para tal necessitaremos saber o nome do nosso servidor remoto:
```
git remote 
```  

* Para mandar agora:
```
git push origin master 
```
> Ou seja o git enviará os arquivos para o servidor origin que estão agora no branch máster.
* Quando se termina uma modificação em um repositório onde mais de um programador trabalha é necessário dar um “pull” que é: traga todos os dados do servidor até o momento.

```
git pull origin master
``` 
> origin - -> de onde vai trazer
> máster - -> pra onde vai mandar

* O git pull tem um pequeno porem ele faz uma busca e praticamente faz um merge desses dados que estão no servidor no servidor com o repositório trabalhado. As vezes isso não é interessante então quando não quiser fazer isso é necessário ter um branch separado e fazer um feltch

```
git feltch origin [branch]  - -> onde se quer colocar
```
> O feltch serve quando não se quer fazer um merge automático dos dados que estão no servidor com o projeto trabalhado.







