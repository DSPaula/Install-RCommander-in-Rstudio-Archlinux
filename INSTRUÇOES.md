# Install-RCommander-in-Rstudio-Archlinux
Instalar em Archlinux Rcommander desde Rstudio
------------------------------------------------
Ordem correta para dar inicio a instalaçao de Rcommander en Rstudio a partir de Archilinux

Aqui estão os passos para instalar o Rcmdr:

Abra o RStudio.
No console do RStudio, execute o seguinte comando para instalar o pacote Rcmdr e suas dependências:
sudo pacman -S gcc-fortran
sudo pacman -S tcl tk
install.packages("setRepositories", repos = "https://cran.rstudio.com/")
setRepositories()
install.packages("minqa")
install.packages(c("car", "pbkrtest", "quantreg", "lme4", "phyr"), dependencies = TRUE)
install.packages("RcmdrMisc")
install.packages("rr2")
sudo chmod -R u+w x86_64-pc-linux-gnu-library
install.packages(c("tcltk2", "Rcmdr"), dependencies = TRUE)
library(Rcmdr)

Instale o pacote RcmdrPlugin.EcoVirtual

install.packages("RcmdrPlugin.EcoVirtual") 
library("RcmdrPlugin.EcoVirtual") 

Se queres entender os erros leia abaixo ou apenas instale os comandos acima sem neunhum stress :)

Entendendo o processo: 
Quando tratamos de instalar o programa apenas usando este comando: install.packages("Rcmdr")
O sistema ira devolver este err: installation of package ‘RcmdrMisc’ had non-zero exit status
ERROR: dependencies ‘RcmdrMisc’, ‘car’, ‘effects’, ‘tcltk2’, ‘lme4’ are not available for package ‘Rcmdr’

Significado do processo: 
Esse erro indica que durante a instalação do pacote Rcmdr no R, houve um erro no processo de instalação do pacote RcmdrMisc, que é uma dependência necessária para instalar o Rcmdr.

O erro "installation of package ‘RcmdrMisc’ had non-zero exit status" indica que a instalação do pacote RcmdrMisc não foi bem-sucedida e teve um status de saída não-zero, o que significa que houve algum problema na instalação.

O erro "dependencies ‘RcmdrMisc’, ‘car’, ‘effects’, ‘tcltk2’, ‘lme4’ are not available for package ‘Rcmdr’" indica que outras dependências do pacote Rcmdr, como car, effects, tcltk2 e lme4, também não estão disponíveis para instalação.

Para resolver esse problema, se pode tentar instalar as dependências individualmente antes de instalar o pacote Rcmdr. Isso pode ajudar a identificar se há problemas com a instalação de alguma das dependências. Além disso, certifique-se de ter a versão mais recente do R e de todas as dependências necessárias para a instalação do pacote.

Instalando Dependencias antes do programa principal:
Instalar cada pacote individualmente usando o comando install.packages() no R. Por exemplo, para instalar o pacote RcmdrMisc, se pode executar o seguinte comando: install.packages("RcmdrMisc").

Havendo dependências ausentes, você pode tentar instalá-las da mesma maneira. Por exemplo, para instalar o pacote "car", se pode executar o seguinte comando: install.packages("car")

Pode-se repetir este processo para cada pacote ausente mencionado na mensagem de erro. Se nenhum dos pacotes estiver disponível em nenhum repositório, pode precisar verificar se há algum problema com as configurações do repositório ou tentar instalar os pacotes manualmente a partir de arquivos binários ou código-fonte.

Tambem, é possível instalar um pacote com suas dependências no mesmo comando usando o argumento 'dependencies = TRUE' da função 'install.packages()'. Um exemplo, seria assim: install.packages(c("car", "pbkrtest", "quantreg", "lme4"), dependencies = TRUE)
Isso deve instalar os pacotes especificados, bem como suas dependências necessárias.

Certamente havera erros como este se nao seguir a ordem correta para realizar a instalaçao: ERROR: dependencies ‘lme4’, ‘phyr’ are not available for package ‘rr2’
* removing ‘/home/Fernando/R/x86_64-pc-linux-gnu-library/4.2/rr2’
Warning in install.packages : installation of package ‘rr2’ had non-zero exit status

A mensagem de erro acima indica que a instalação do pacote 'rr2' falhou porque duas de suas dependências, 'lme4' e 'phyr', não estavam disponíveis. Isso significa que esses dois pacotes não foram instalados no sistema ou a versão instalada não é compatível com a versão exigida pelo 'rr2'.

Como resultado, o pacote 'rr2' não pôde ser instalado e a função install.packages() retorna um status de saída diferente de zero, indicando que houve um erro durante o processo de instalação.

Esse erro ocorre porque as dependências do pacote rr2 não estão disponíveis no repositório atual. Uma solução é adicionar um repositório que contenha essas dependências.

Você pode tentar adicionar o repositório https://cran.rstudio.com/, que é o CRAN (Comprehensive R Archive Network) oficial, e tentar instalar novamente o pacote rr2. Para isso, execute os seguintes comandos no R:

Adicionar o CRAN como repositório
install.packages("setRepositories", repos = "https://cran.rstudio.com/") setRepositories()      (1)

# Tentar instalar o pacote rr2 novamente
install.packages("rr2")                                                                         (2)

Se isso não funcionar, pode ser necessário tentar instalar as dependências individualmente ou por meio de outros repositórios.


A opçao a escolher: 
--- Please select repositories for use in this session ---


1: + CRAN
2:   BioC software
3:   BioC annotation
4:   BioC experiment
5:   CRAN (extras)
6:   R-Forge
7:   rforge.net

Enter one or more numbers separated by spaces and then ENTER, or 0 to cancel
1: 1 5 (estas sao as opcoes que necessarias para realizar a instalaçao)

A opção 1 corresponde ao repositório CRAN, que é o repositório padrão para instalar pacotes do R. Portanto, se quiser instalar pacotes da CRAN, selecione a opção 1 digitando "1" e pressionando ENTER. Ou se quiser selecionar mais de um repositório, digite os números correspondentes às opções separados por espaços. Por exemplo, se você quiser selecionar o CRAN e o BioC software, digite "1 5" e pressione ENTER. Se você quiser cancelar a seleção de repositórios, digite "0" e pressione ENTER.

Podeapresentar este problema pode estar ocorrendo porque as dependências 'lme4' e 'phyr' não estão sendo encontradas no repositório CRAN. Pode-se tentar instalar essas dependências a partir de outros repositórios ou verificar se há problemas de configuração no seu ambiente R.

Uma opção é instalar a dependência 'lme4' diretamente do repositório do desenvolvedor com o seguinte comando: 
install.packages("lme4", repos="http://lme4.r-forge.r-project.org/repos")

Em seguida, tente instalar novamente o pacote rr2.

Caso ainda haja problemas, verifique se todas as dependências do pacote rr2 estão instaladas corretamente. Você pode fazer isso executando o seguinte comando no console do R: install.packages(c("lme4", "phyr"))

Este comando irá instalar as dependências necessárias para o pacote 'rr2'. Depois de instaladas as dependências, tente instalar novamente o pacote 'rr2'.

Puede surgir esta mensagem: ERROR: dependency ‘minqa’ is not available for package ‘lme4’
* removing ‘/home/Fernando/R/x86_64-pc-linux-gnu-library/4.2/lme4’
Warning in install.packages : installation of package ‘lme4’ had non-zero exit status


Essa mensagem indica que a instalação do pacote lme4 não foi bem-sucedida devido à falta de uma dependência chamada minqa. Uma possível solução é instalar essa dependência antes de tentar instalar o pacote lme4.

Para fazer isso, você pode usar o comando install.packages() novamente, especificando o nome da dependência como argumento. Exemplo: install.packages("minqa"). Depois de instalar a dependência 'minqa', tente instalar novamente o pacote 'lme4' usando o comando install.packages("lme4").

Puede surgir esta mensagem: gfortran -fno-optimize-sibling-calls  -fpic  -g -O2  -c altmov.f -o altmov.o
make: gfortran: Arquivo ou diretório inexistente make: *** [/usr/lib64/R/etc/Makeconf:192: altmov.o] Error 127
ERROR: compilation failed for package ‘minqa’ * removing ‘/home/Fernando/R/x86_64-pc-linux-gnu-library/4.2/minqa’
Warning in install.packages : installation of package ‘minqa’ had non-zero exit status

O erro indica que não foi possível encontrar o compilador gfortran. Certifique-se de que o compilador está instalado em seu sistema e que o diretório contendo o executável do compilador está incluído em sua variável de ambiente PATH. Você pode verificar se o compilador está instalado usando o seguinte comando em um terminal: gfortran --version

Precisa-se instalar o compilador 'gfortran' para resolver esse erro. Você pode fazer isso com o seguinte comando: sudo pacman -S gcc-fortran

Em seguida, tente instalar o pacote R novamente com este codigo: install.packages("tcltk2", "Rcmdr")

Puede surgir esta mensagem:> install.packages("tcltk2", "Rcmdr")
Warning in install.packages :
  'lib = "Rcmdr"' is not writable
Would you like to use a personal library instead? (yes/No/cancel)

Essa mensagem indica que o diretório padrão de instalação de pacotes R não tem permissão de escrita. Uma solução é instalar os pacotes em uma biblioteca pessoal, onde você tem permissão para gravar.

Você pode verificar se o diretório ~/R existe executando o seguinte comando no terminal: ls ~/R


Para criar uma biblioteca pessoal, você pode executar o seguinte comando: 


Para dar permissão de escrita ao diretório '~/R', você pode executar o seguinte comando no terminal: chmod u+w ~/R

Isso dará permissão de escrita para o proprietário (usuário atual) do diretório '~/R'. Certifique-se de que o usuário que está executando o RStudio seja o proprietário do diretório ou tenha permissão para escrever nele.

Você também pode usar a opção -R para dar permissão de escrita recursivamente a todos os arquivos e subdiretórios dentro do diretório '~/R', caso seja necessário: chmod -R u+w ~/R

Note que a alteração nas permissões de um diretório pode afetar a segurança do sistema, portanto, deve ser realizada com cuidado. Certifique-se de entender as implicações de alterar as permissões de um diretório antes de prosseguir.

Se pode usar um diretório diferente, se pode digitar "yes" e depois selecionar ou criar um diretório que você tenha permissão de escrita. Por exemplo, você pode digitar "yes" e em seguida selecionar um diretório em sua pasta pessoal, como "~/R/library". Ou, se preferir, pode cancelar e conceder permissões de escrita ao diretório "x86_64-pc-linux-gnu-library" para instalar as bibliotecas no local padrão.

Para dar permissão de escrita ao diretório "x86_64-pc-linux-gnu-library", você pode usar o comando "chmod". Aqui está como fazer:

1- Abra o terminal e navegue até a pasta que contém o diretório "x86_64-pc-linux-gnu-library".

2- Execute o seguinte comando para dar permissão de escrita ao diretório:
sudo chmod -R u+w x86_64-pc-linux-gnu-library
Este comando dará ao usuário atual (u) permissão de escrita (+w) recursivamente (-R) em todo o diretório "x86_64-pc-linux-gnu-library".

Depois de executar o comando acima, tente instalar as bibliotecas novamente e verifique se o erro de permissão foi resolvido.

Puede surgir esta mensagem: Warning in install.packages :
  'lib = "Rcmdr"' is not writable
Would you like to use a personal library instead? (yes/No/cancel)

Essa mensagem de erro indica que você não tem permissão para instalar pacotes na biblioteca global do R (neste caso, "Rcmdr"). Como uma solução alternativa, você pode criar uma biblioteca pessoal em um diretório onde tenha permissão de gravação. Para fazer isso, siga os seguintes passos:

pode verificar se o diretório tem permissão de escrita usando o comando: ls -ld ~/R/x86_64-pc-linux-gnu-library. Se as permissões estiverem definidas corretamente, você deverá ver algo parecido com "drwxrwxr-x" na saída

Se mesmo dando permissão de escrita ao diretório x86_64-pc-linux-gnu-library, o erro persiste, você pode tentar definir um diretório diferente como destino para as bibliotecas. Para isso, você pode usar o seguinte comando:
install.packages("tcltk2", lib="/caminho/para/o/novo/diretorio")

Substitua "/caminho/para/o/novo/diretorio" pelo caminho para um diretório para o qual você tenha permissões de escrita. Por exemplo:
install.packages("tcltk2", lib="/home/Tu usuario/R/bibliotecas")
Lembre-se de criar o diretório antes de executar o comando acima.

Para criar o diretório Rcmdr, você pode executar o seguinte comando em um terminal:
mkdir ~/R/Rcmdr

Isso irá criar um diretório chamado 'Rcmdr' dentro do diretório 'R' na sua pasta pessoal ('~/'). Certifique-se de que você tem permissão para criar diretórios na sua pasta pessoal.

Criando o diretório, tente novamente instalar o pacote utilizando o seguinte comando: install.packages("tcltk2", lib="~/R/Rcmdr")

Certifique-se de que o diretório "Rcmdr" tenha permissões de escrita e que ele tenha sido criado dentro do diretório "~/R". Se necessário, dê permissão de escrita ao diretório "R" também.

Pode surgir esse erro:
* installing *source* package ‘tcltk2’ ...
** package ‘tcltk2’ successfully unpacked and MD5 sums checked
** using staged installation
** R
** inst
** byte-compile and prepare package for lazy loading
Erro: package or namespace load failed for ‘tcltk’:
 .onLoad falhou em loadNamespace() para 'tcltk', detalhes:
  chamada: dyn.load(file, DLLpath = DLLpath, ...)
  erro: impossível carregar objeto compartilhado '/usr/lib/R/library/tcltk/libs/tcltk.so':
  libtcl8.6.so: não é possível abrir arquivo compartilhado: Arquivo ou diretório inexistente
Execução interrompida
ERROR: lazy loading failed for package ‘tcltk2’
* removing ‘/home/Fernando/R/Rcmdr/tcltk2’
Warning in install.packages :
  installation of package ‘tcltk2’ had non-zero exit status

Parece que a instalação do pacote tcltk2 falhou devido a um erro no carregamento do namespace do pacote tcltk, com a mensagem de erro "impossível carregar objeto compartilhado '/usr/lib/R/library/tcltk/libs/tcltk.so': libtcl8.6.so: não é possível abrir arquivo compartilhado: Arquivo ou diretório inexistente".

Isso pode estar relacionado a uma dependência ausente no sistema. Você pode tentar instalar as bibliotecas do sistema necessárias executando o seguinte comando em um terminal: sudo pacman -S tcl tk
Depois de instalar as bibliotecas do sistema, tente instalar o pacote 'tcltk2' novamente no R.

O próximo passo seria tentar instalar novamente o pacote Rcmdr com o seguinte comando: install.packages("Rcmdr")
Se a instalação ainda não for bem sucedida, sugiro verificar se as dependências do pacote Rcmdr estão instaladas e atualizadas. Você pode fazer isso com o seguinte comando: install.packages("Rcmdr", dependencies = TRUE)

Este comando irá instalar o pacote Rcmdr e todas as suas dependências necessárias.



































































