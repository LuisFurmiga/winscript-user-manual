# Guia de utilização do WinScript para otimizar o Windows

## Menu de navegação

1. [Introdução](#introducao)
2. [Para quem este guia é indicado?](#publico)
3. [O que fazer antes de usar o WinScript](#preparacao)

   * [Salve os arquivos importantes](#backup)
   * [Atualize o Windows](#atualizar-windows)
   * [Crie um ponto de restauração](#ponto-restauracao)
   * [Anote a configuração atual](#configuracao-atual)
4. [Formas de utilizar o WinScript](#formas-utilizacao)

   * [Aplicativo para desktop](#aplicativo-desktop)
   * [Versão on-line](#versao-online)
   * [Execução direta pelo PowerShell](#execucao-powershell)
5. [Conhecendo as categorias do WinScript](#categorias-winscript)

   * [Tools — manutenção e recuperação](#tools)
   * [Debloat — remoção de aplicativos e componentes](#debloat)
   * [Privacy — configurações de privacidade](#privacy)
   * [Telemetry — coleta de dados e diagnósticos](#telemetry)
   * [Gaming — ajustes para jogos](#gaming)
   * [Performance — desempenho](#performance)
   * [Miscellaneous — ajustes diversos](#miscellaneous)
   * [Browse Apps — instalação de programas](#browse-apps)
6. [Procedimento recomendado para usuários iniciantes](#procedimento-iniciantes)
7. [Procedimento recomendado para técnicos](#procedimento-tecnicos)

   * [Faça o levantamento do equipamento](#levantamento-equipamento)
   * [Estabeleça o objetivo](#estabelecer-objetivo)
   * [Crie perfis diferentes](#perfis)
   * [Exporte a configuração](#exportar-configuracao)
   * [Teste antes de implantar](#testes)
8. [Como avaliar se houve melhoria](#avaliar-melhoria)

   * [Tempo de inicialização](#tempo-inicializacao)
   * [Uso de memória](#uso-memoria)
   * [Uso de processador](#uso-processador)
   * [Uso do disco](#uso-disco)
   * [Temperatura](#temperatura)
   * [Jogos](#testes-jogos)
9. [O que o WinScript não consegue resolver](#limitacoes)
10. [Alterações que devem ser evitadas por usuários iniciantes](#alteracoes-evitar)
11. [Como aplicar alterações com segurança](#aplicar-seguranca)
12. [Como desfazer alterações](#desfazer-alteracoes)

    * [Usar a opção inversa no WinScript](#opcao-inversa)
    * [Reinstalar um aplicativo](#reinstalar-aplicativo)
    * [Usar a Restauração do Sistema](#restauracao-sistema)
    * [Usar o Ambiente de Recuperação](#ambiente-recuperacao)
    * [Restaurar backup ou reinstalar o Windows](#restaurar-backup)
13. [Solução de problemas comuns](#solucao-problemas)
14. [Modelo de configuração conservadora](#configuracao-conservadora)
15. [Modelo de checklist para técnicos](#checklist-tecnicos)
16. [Boas práticas de segurança](#boas-praticas)
17. [Perguntas frequentes](#perguntas-frequentes)
18. [Conclusão](#conclusao)

---

<a name="introducao"></a>

## 1. Introdução

O **WinScript** é uma ferramenta gratuita e de código aberto criada para facilitar a configuração, limpeza e otimização do Windows 10 e do Windows 11.

Por meio de uma interface gráfica, o usuário pode selecionar diferentes ajustes e gerar um script personalizado. Esse script pode:

* remover aplicativos desnecessários;
* reduzir programas executados em segundo plano;
* modificar configurações de privacidade;
* limitar a coleta de dados e telemetria;
* ajustar recursos relacionados ao desempenho;
* realizar tarefas de manutenção e reparo;
* instalar vários programas de uma só vez;
* personalizar diferentes comportamentos do Windows.

O WinScript reúne essas opções em categorias como **Tools**, **Debloat**, **Privacy**, **Telemetry**, **Gaming**, **Performance**, **Miscellaneous** e **Browse Apps**. A ferramenta está disponível em versão para desktop e em uma versão executada pelo navegador.

> **Importante:** o WinScript não é um programa que “aumenta magicamente” a velocidade do computador. Ele aplica alterações reais no Windows. Algumas podem melhorar o desempenho, enquanto outras podem remover funções utilizadas pelo usuário ou reduzir a segurança do sistema. Portanto, selecione somente as opções que você entende e realmente necessita.

---
<a name="publico"></a>
## 2. Para quem este guia é indicado?

Este guia foi preparado para dois públicos:

### Usuários domésticos

Pessoas que desejam:

* reduzir aplicativos desnecessários;
* deixar o Windows mais organizado;
* melhorar a inicialização;
* diminuir atividades em segundo plano;
* liberar espaço em disco;
* melhorar a privacidade;
* instalar programas com mais facilidade.

### Técnicos de informática

Profissionais que desejam:

* padronizar configurações;
* preparar computadores novos;
* otimizar instalações do Windows;
* criar configurações reutilizáveis;
* automatizar a instalação de aplicativos;
* aplicar ajustes de forma controlada;
* gerar scripts para uso em diferentes máquinas.

---
<a name="preparacao"></a>
## 3. O que fazer antes de usar o WinScript

Antes de executar qualquer otimização, faça uma preparação básica do computador.
<a name="backup"></a>
### 3.1 Salve os arquivos importantes

Faça uma cópia dos documentos, fotografias, planilhas, arquivos de trabalho e outros dados importantes.

O backup pode ser realizado em:

* unidade externa;
* pendrive;
* servidor da empresa;
* armazenamento em nuvem;
* outro computador.

Um ponto de restauração ajuda a recuperar configurações do sistema, mas **não substitui um backup completo dos arquivos pessoais**.
<a name="atualizar-windows"></a>
### 3.2 Atualize o Windows

Antes da otimização:

1. Abra **Configurações**.
2. Entre em **Windows Update**.
3. Clique em **Verificar se há atualizações**.
4. Instale as atualizações disponíveis.
5. Reinicie o computador quando solicitado.

Também é recomendável atualizar os drivers importantes, especialmente:

* chipset;
* vídeo;
* rede;
* áudio;
* armazenamento.

Em notebooks e computadores de fabricantes conhecidos, dê preferência aos drivers fornecidos pelo fabricante do equipamento.
<a name="ponto-restauracao"></a>
### 3.3 Crie um ponto de restauração

A Microsoft recomenda habilitar a Proteção do Sistema para que seja possível recuperar o Windows após alterações problemáticas. Um ponto de restauração registra arquivos do sistema, programas instalados, configurações e partes do Registro do Windows.

Para criar um ponto de restauração manualmente:

1. Pressione `Windows + R`.
2. Digite:

```text
systempropertiesprotection.exe
```

3. Pressione **Enter**.
4. Selecione a unidade onde o Windows está instalado, normalmente `C:`.
5. Clique em **Configurar**.
6. Marque **Ativar a proteção do sistema**, caso esteja desativada.
7. Clique em **Aplicar**.
8. Clique em **Criar**.
9. Digite um nome, como:

```text
Antes do WinScript
```

10. Aguarde a confirmação da criação.

O próprio WinScript também possui uma opção chamada **Create Restore Point**, localizada na categoria **Tools**. Entretanto, é recomendável verificar previamente se a Proteção do Sistema está ativada.
<a name="configuracao-atual"></a>
### 3.4 Anote a configuração atual

Antes das mudanças, registre informações como:

* programas que o usuário utiliza;
* funcionamento da impressora;
* funcionamento do Bluetooth;
* sincronização com o OneDrive;
* login com conta Microsoft;
* funcionamento da câmera e do microfone;
* recursos de jogos;
* compartilhamento de arquivos;
* acesso a computadores da empresa;
* recursos de virtualização;
* uso de biometria ou reconhecimento facial.

Esse registro facilita a identificação de eventuais problemas depois da otimização.

---
<a name="formas-utilizacao"></a>
## 4. Formas de utilizar o WinScript

Existem três formas principais de utilizar a ferramenta.
<a name="aplicativo-desktop"></a>
## 4.1 Aplicativo para desktop

A versão para desktop é a alternativa mais simples para a maioria dos usuários.

Ela permite:

* selecionar ajustes por uma interface gráfica;
* importar e exportar configurações;
* executar os ajustes selecionados;
* gerar scripts;
* reutilizar configurações em outros computadores.

### Instalação pelo Winget

Abra o **Terminal** ou **PowerShell** como administrador e execute:

```powershell
winget install winscript
```

O Winget é o gerenciador de pacotes do Windows e pode instalar o aplicativo diretamente. Esse é um dos métodos apresentados pela documentação oficial do projeto.

Depois da instalação:

1. Abra o menu **Iniciar**.
2. Pesquise por **WinScript**.
3. Clique com o botão direito no aplicativo.
4. Selecione **Executar como administrador**.

O acesso administrativo é necessário porque diversas alterações afetam componentes e configurações protegidas do Windows.
<a name="versao-online"></a>
## 4.2 Versão on-line

A versão on-line permite montar a configuração diretamente no navegador.

O processo geral é:

1. Acessar a versão on-line oficial do WinScript.
2. Selecionar as opções desejadas.
3. Revisar todas as alterações.
4. Baixar o script gerado.
5. Examinar o conteúdo do arquivo.
6. Executá-lo como administrador.

A versão on-line oferece categorias semelhantes às do aplicativo, incluindo ferramentas de limpeza, reparo, privacidade, desempenho e instalação de aplicativos.

> **Recomendação para técnicos:** salve uma cópia do script gerado e registre a versão do WinScript utilizada. Isso facilita auditorias, suporte e repetição do procedimento.
<a name="execucao-powershell"></a>
## 4.3 Execução direta pelo PowerShell

A documentação também apresenta um comando que baixa e executa o WinScript diretamente:

```powershell
irm "https://winscript.cc/irm" | iex
```

Nesse comando:

* `irm` é uma abreviação de `Invoke-RestMethod`;
* o conteúdo é baixado do endereço informado;
* `iex` executa imediatamente o conteúdo recebido.

Embora seja um método prático, ele executa código obtido da internet diretamente no computador. Por isso, deve ser usado somente quando:

* o endereço tiver sido conferido;
* a conexão for confiável;
* o usuário estiver utilizando a fonte oficial;
* o técnico compreender o que será executado.

Para usuários menos experientes, é preferível utilizar o aplicativo instalado pelo Winget ou gerar e revisar o script antes da execução.

---
<a name="categorias-winscript"></a>
## 5. Conhecendo as categorias do WinScript
<a name="tools"></a>
## 5.1 Tools — manutenção e recuperação

A categoria **Tools** reúne funções de manutenção do computador.

Entre as opções disponíveis estão:

### Create Restore Point

Cria um ponto de restauração antes das alterações.

**Recomendação:** selecione esta opção em praticamente toda execução que envolva modificações importantes.

### Clean-up

Remove arquivos temporários e outros dados que podem ocupar espaço desnecessariamente.

Pode ajudar quando:

* o disco está quase cheio;
* existem muitos arquivos temporários;
* atualizações antigas deixaram resíduos;
* o computador passou por várias instalações e desinstalações.

A limpeza normalmente libera espaço, mas não deve ser tratada como uma melhoria garantida de velocidade.

### Repair

Verifica a integridade dos arquivos do Windows e tenta corrigir arquivos corrompidos.

Essa opção pode ser útil quando o computador apresenta:

* erros inexplicáveis;
* travamentos;
* recursos do Windows que não abrem;
* mensagens relacionadas a arquivos ausentes;
* problemas depois de atualizações.

### Reset Network

Redefine determinados componentes de rede, limpa informações de DNS e renova configurações de endereço IP.

Use quando houver:

* falhas de acesso à internet;
* problemas de DNS;
* conexão inconsistente;
* configuração de rede corrompida.

> Uma redefinição de rede pode exigir a reconfiguração de VPNs, proxies, endereços IP manuais ou componentes corporativos.

### Clear Browser History

Apaga históricos de navegadores compatíveis.

Use com cuidado, pois isso pode remover informações que o usuário deseja manter.

A versão on-line lista, entre suas ferramentas, limpeza, reparo, criação de ponto de restauração, limpeza de histórico e redefinição de rede.

---
<a name="debloat"></a>
## 5.2 Debloat — remoção de aplicativos e componentes

O termo **debloat** significa remover ou desativar componentes considerados desnecessários.

O WinScript pode oferecer opções relacionadas a:

* aplicativos pré-instalados;
* Microsoft Copilot;
* Widgets;
* recursos de consumo e sugestões;
* OneDrive;
* Microsoft Edge;
* Microsoft Store;
* aplicativos promocionais;
* componentes opcionais do Windows;
* recursos como Recall, dependendo da versão do sistema.

Essas opções podem reduzir a quantidade de aplicativos instalados, processos em segundo plano e elementos exibidos na interface.

### Opções geralmente menos arriscadas

Para a maioria dos usuários, costuma ser mais prudente começar com:

* remoção de jogos promocionais;
* remoção de aplicativos que nunca são utilizados;
* desativação de sugestões e conteúdo promocional;
* desativação de Widgets, quando não utilizados;
* remoção de aplicativos de terceiros instalados pelo fabricante;
* desativação de recursos de consumo do Windows.

### Opções que exigem atenção

#### Remover o OneDrive

Não remova o OneDrive quando o usuário:

* sincroniza documentos;
* utiliza backup das pastas Área de Trabalho, Documentos ou Imagens;
* trabalha com arquivos compartilhados;
* utiliza Microsoft 365;
* depende do OneDrive corporativo.

Antes da remoção, confirme se os arquivos estão realmente armazenados no computador e não apenas disponíveis na nuvem.

#### Remover a Microsoft Store

A Microsoft Store é utilizada para instalar e atualizar determinados aplicativos.

Sua remoção pode dificultar:

* instalação de aplicativos;
* atualização de programas da Store;
* recuperação de alguns componentes;
* uso de recursos associados à conta Microsoft.

Para usuários comuns, geralmente é melhor manter a Microsoft Store.

#### Remover o Microsoft Edge

Mesmo que outro navegador seja utilizado, certos componentes do Edge e do WebView podem ser usados por aplicativos e partes do Windows.

A remoção profunda pode provocar:

* falhas em aplicativos;
* páginas internas que não abrem;
* problemas em recursos baseados em conteúdo web;
* dificuldades em atualizações.

Para a maioria das pessoas, é mais seguro apenas definir outro navegador como padrão.

#### Remover todos os aplicativos de uma só vez

Evite opções amplas de remoção quando não houver uma lista clara do que será excluído.

Aplicativos aparentemente desnecessários podem estar relacionados a:

* câmera;
* calculadora;
* captura de tela;
* reprodução de mídia;
* impressão;
* fotos;
* relógio e alarmes;
* codecs;
* componentes utilizados por outros programas.

### Regra prática para debloat

Remova apenas aquilo que:

1. você reconhece;
2. sabe para que serve;
3. tem certeza de que não utiliza;
4. consegue reinstalar posteriormente.

---
<a name="privacy"></a>
## 5.3 Privacy — configurações de privacidade

A categoria **Privacy** modifica permissões e comportamentos relacionados ao acesso de aplicativos aos dados do usuário.

As opções podem envolver:

* localização;
* câmera;
* microfone;
* contatos;
* calendário;
* histórico de atividades;
* reconhecimento de fala;
* sincronização de configurações;
* identificação de publicidade;
* execução de aplicativos em segundo plano;
* acesso a informações da conta;
* histórico de chamadas;
* mensagens;
* documentos, imagens e vídeos.

O WinScript também pode limitar sincronização de temas e senhas, rastreamento de atividades e serviços relacionados à localização.

### Recomendações para usuários comuns

Normalmente é razoável considerar:

* desativar o identificador de publicidade;
* desativar sugestões personalizadas;
* limitar permissões de aplicativos não utilizados;
* impedir que aplicativos desnecessários funcionem em segundo plano;
* desativar histórico de atividades, quando não utilizado;
* limitar localização para aplicativos que não precisam dela.

### Situações em que as permissões devem ser mantidas

Não bloqueie globalmente câmera e microfone quando o usuário utiliza:

* Microsoft Teams;
* Zoom;
* Google Meet;
* Discord;
* gravação de áudio;
* videochamadas;
* reconhecimento de voz.

Não bloqueie localização quando o usuário utiliza:

* localização de dispositivo;
* mapas;
* previsão do tempo por localização;
* recursos de segurança de notebooks;
* aplicativos corporativos dependentes de localização.

Para computadores corporativos, qualquer mudança de privacidade deve ser compatível com as políticas da organização.

---
<a name="telemetry"></a>
## 5.4 Telemetry — coleta de dados e diagnósticos

A telemetria corresponde ao envio de dados de diagnóstico, uso e funcionamento do sistema.

O WinScript apresenta opções para reduzir dados enviados por:

* Windows;
* Microsoft Office;
* pesquisa do Windows;
* serviços de atualização;
* relatórios de erro;
* aplicativos de terceiros;
* Adobe;
* Google;
* NVIDIA;
* Visual Studio Code;
* outros programas compatíveis.

Também podem existir opções relacionadas a reconhecimento de fala na nuvem, biometria e conectividade de gerenciamento de direitos digitais.

### Possíveis benefícios

* redução de determinadas tarefas em segundo plano;
* menor coleta de dados;
* aumento da privacidade;
* diminuição de comunicações não essenciais.

### Possíveis efeitos colaterais

* redução de informações usadas para diagnóstico;
* relatórios de erro menos detalhados;
* prejuízo em recursos de personalização;
* falhas em recursos corporativos;
* problemas com aplicativos dependentes de serviços on-line;
* dificuldade para suporte técnico investigar erros.

### Orientação recomendada

Para usuários domésticos, prefira reduzir opções de publicidade, sugestões e coleta opcional, sem desativar indiscriminadamente todos os serviços de diagnóstico.

Para empresas, não aplique essas alterações sem verificar:

* políticas de segurança;
* ferramentas de inventário;
* sistemas de gerenciamento;
* Microsoft Intune;
* domínios corporativos;
* serviços de monitoramento;
* requisitos legais e contratuais.

---
<a name="gaming"></a>
## 5.5 Gaming — ajustes para jogos

A categoria **Gaming** reúne alterações direcionadas a computadores utilizados para jogos.

Esses ajustes podem envolver:

* Xbox Game Bar;
* gravação em segundo plano;
* otimizações de tela;
* aceleração de hardware;
* latência de entrada;
* prioridade de processos;
* serviços relacionados a jogos;
* plano de energia.

### Nem toda otimização melhora todos os jogos

O resultado pode variar de acordo com:

* processador;
* placa de vídeo;
* quantidade de memória;
* driver instalado;
* versão do Windows;
* jogo executado;
* resolução;
* tipo de armazenamento;
* temperatura do equipamento.

Por isso, altere poucas opções de cada vez e compare o funcionamento antes e depois.

### Xbox Game Bar

Pode ser desativada quando o usuário não utiliza:

* captura de vídeo;
* gravação de partidas;
* sobreposição;
* recursos sociais do Xbox;
* monitoramento pela Game Bar.

Mantenha o recurso quando ele fizer parte da rotina do jogador.

### Gravação em segundo plano

A desativação pode reduzir alguma atividade durante os jogos, mas impede a gravação retroativa de partidas.

### HAGS

A sigla HAGS corresponde ao agendamento de GPU acelerado por hardware.

Dependendo do computador, do driver e do jogo, ativar ou desativar esse recurso pode:

* melhorar o desempenho;
* não produzir diferença;
* provocar instabilidade;
* piorar a fluidez.

Não existe uma configuração universal. Teste o mesmo jogo, na mesma cena e com as mesmas opções gráficas antes de decidir.

---
<a name="performance"></a>
## 5.6 Performance — desempenho

A categoria **Performance** concentra algumas das alterações mais sensíveis da ferramenta.

Ela pode incluir opções como:

* plano de energia de desempenho máximo;
* alteração da inicialização de serviços;
* redução de atrasos do mouse;
* desativação de indexação;
* desativação de hibernação;
* desativação do SysMain ou Superfetch;
* alterações no Storage Sense;
* ajustes do Microsoft Defender;
* desativação de Isolamento do Núcleo;
* configurações relacionadas à GPU;
* alterações de comportamento do sistema.

A documentação oficial apresenta esses recursos como parte das opções de desempenho do WinScript.

### Plano Ultimate Performance

O plano **Ultimate Performance** reduz determinadas políticas de economia de energia e prioriza a disponibilidade de desempenho.

Pode ser útil em:

* estações de trabalho;
* computadores de alto desempenho;
* desktops permanentemente ligados à tomada;
* tarefas pesadas e contínuas;
* testes específicos.

Pode ser inadequado em:

* notebooks;
* computadores com refrigeração limitada;
* máquinas utilizadas com bateria;
* ambientes que precisam economizar energia;
* equipamentos com superaquecimento.

Possíveis consequências:

* maior consumo elétrico;
* menor duração da bateria;
* aumento de temperatura;
* maior ruído das ventoinhas;
* pouco ou nenhum ganho perceptível.

Para usuários comuns, o plano **Equilibrado** do Windows geralmente é a melhor escolha.

### Serviços em inicialização manual

Alterar serviços de **Automático** para **Manual** pode reduzir processos iniciados com o Windows.

Entretanto, alguns serviços são necessários para:

* impressão;
* Bluetooth;
* rede;
* atualizações;
* login;
* áudio;
* segurança;
* criptografia;
* compartilhamento;
* biometria;
* dispositivos externos;
* máquinas virtuais.

Essa alteração é recomendada apenas quando o técnico:

1. conhece os serviços afetados;
2. testa os recursos do computador;
3. possui forma de restaurar a configuração;
4. documenta o que foi modificado.

### Windows Search Indexing

A indexação mantém um catálogo para acelerar a pesquisa de arquivos, e-mails e conteúdo.

Desativá-la pode reduzir alguma atividade de disco em determinados computadores, mas torna pesquisas mais lentas.

Mantenha a indexação quando o usuário:

* pesquisa arquivos com frequência;
* utiliza muitos documentos;
* utiliza pesquisa no Outlook;
* depende da busca do menu Iniciar.

A desativação pode ser considerada em computadores muito limitados ou em máquinas que raramente utilizam a pesquisa.

### SysMain ou Superfetch

O SysMain analisa padrões de utilização e antecipa o carregamento de aplicativos.

Desativá-lo pode ser testado quando:

* existe uso constante e anormal do disco;
* o computador utiliza armazenamento lento;
* o serviço está diretamente relacionado a travamentos;
* o técnico confirmou o problema.

Não o desative automaticamente em todos os computadores. Em muitos sistemas, especialmente com armazenamento moderno, o Windows gerencia esse recurso adequadamente.

### Hibernação

A desativação da hibernação pode liberar vários gigabytes, pois remove o arquivo `hiberfil.sys`.

Entretanto, ela pode afetar:

* a opção **Hibernar**;
* a Inicialização Rápida;
* determinados comportamentos de energia;
* a rotina de usuários de notebook.

Desative apenas quando o espaço em disco for mais importante e o usuário não utilizar esses recursos.

### Storage Sense

O Sensor de Armazenamento remove automaticamente determinados arquivos temporários e ajuda no gerenciamento de espaço.

Desativá-lo não costuma gerar melhoria significativa de desempenho. Em muitos computadores, é mais útil mantê-lo configurado adequadamente.

### Microsoft Defender

Algumas opções do WinScript podem limitar o uso de processador pelo Microsoft Defender ou alterar recursos de proteção.

Não é recomendável:

* desativar o antivírus;
* desativar a proteção em tempo real;
* excluir o disco inteiro da verificação;
* reduzir excessivamente a segurança;
* impedir atualizações de definições.

Em computadores utilizados para internet, e-mail, banco, trabalho ou armazenamento de dados, a segurança deve ter prioridade sobre pequenos ganhos de desempenho.

### Isolamento do Núcleo e Integridade da Memória

A Integridade da Memória utiliza segurança baseada em virtualização para proteger o núcleo do Windows contra código malicioso e ataques que tentam explorar drivers. A Microsoft considera esse recurso um componente importante da proteção do sistema.

Em processadores antigos, o impacto no desempenho pode ser maior. Entretanto, desativar esse recurso reduz a proteção contra ataques ao núcleo do Windows.

Portanto:

* **usuários comuns devem mantê-lo ativado**;
* computadores de empresas devem seguir a política de segurança;
* não deve ser desativado apenas por uma promessa genérica de mais FPS;
* qualquer teste deve ser acompanhado de medição e análise de risco.

---
<a name="miscellaneous"></a>
## 5.7 Miscellaneous — ajustes diversos

A categoria **Miscellaneous** reúne personalizações e comportamentos que não se encaixam nas demais categorias.

Ela pode incluir alterações relacionadas a:

* menu de contexto;
* barra de tarefas;
* Explorador de Arquivos;
* aparência;
* atalhos;
* atualizações;
* notificações;
* tela de bloqueio;
* comportamento de aplicativos;
* recursos opcionais.

Essas modificações nem sempre melhoram o desempenho. Muitas são apenas preferências de interface.

Antes de selecionar uma opção, pergunte:

* Isso melhora o desempenho ou apenas muda a aparência?
* O usuário prefere o comportamento atual?
* A alteração pode confundir outras pessoas?
* Será fácil restaurar a configuração?

---
<a name="browse-apps"></a>
## 5.8 Browse Apps — instalação de programas

A categoria **Browse Apps** permite selecionar vários programas e gerar um script para instalá-los automaticamente.

O WinScript pode utilizar:

* **Winget**;
* **Chocolatey**.

Entre as categorias de aplicativos podem estar:

* navegadores;
* compactadores;
* reprodutores de mídia;
* editores;
* ferramentas de desenvolvimento;
* programas de comunicação;
* utilitários;
* clientes de jogos.

A instalação em lote é um dos recursos oficialmente apresentados pelo projeto.

### Exemplo de conjunto básico

Para um computador doméstico, pode ser útil instalar:

* um navegador alternativo;
* 7-Zip;
* VLC;
* leitor de PDF;
* aplicativo de videoconferência utilizado pelo usuário.

### Orientação para técnicos

Evite instalar programas apenas porque estão disponíveis na lista.

Antes de selecionar um aplicativo, confirme:

* se ele é necessário;
* se já existe outro programa com a mesma função;
* se a licença permite o uso pretendido;
* se a versão atende às necessidades da empresa;
* se não existe uma política corporativa de instalação.

---
<a name="procedimento-iniciantes"></a>
## 6. Procedimento recomendado para usuários iniciantes

A configuração abaixo busca melhorar organização, privacidade e manutenção sem aplicar alterações extremas.

### Etapa 1 — Preparação

1. Faça backup dos arquivos.
2. Atualize o Windows.
3. Atualize os drivers.
4. Reinicie o computador.
5. Crie um ponto de restauração.

### Etapa 2 — Tools

Considere selecionar:

* **Create Restore Point**;
* **Clean-up**;
* **Repair**, somente se houver indícios de arquivos corrompidos.

Não selecione **Reset Network** sem existir um problema de rede.

### Etapa 3 — Debloat

Remova apenas:

* jogos promocionais não utilizados;
* aplicativos conhecidos que não são necessários;
* sugestões e conteúdo promocional;
* Widgets, caso não sejam utilizados.

Mantenha inicialmente:

* Microsoft Store;
* Microsoft Edge e seus componentes;
* aplicativos de câmera e fotos;
* calculadora;
* componentes de mídia;
* OneDrive, quando houver sincronização;
* componentes de segurança.

### Etapa 4 — Privacy

Considere:

* desativar o identificador de publicidade;
* reduzir sugestões personalizadas;
* limitar aplicativos em segundo plano;
* impedir acesso desnecessário a localização, câmera e microfone;
* desativar histórico de atividades, se não for utilizado.

### Etapa 5 — Telemetry

Prefira ajustes moderados:

* reduzir coleta opcional;
* desativar publicidade e sugestões;
* limitar telemetria de aplicativos que o usuário conhece;
* manter recursos necessários para diagnóstico e atualização.

### Etapa 6 — Performance

Para iniciantes:

* mantenha o plano de energia **Equilibrado**;
* mantenha o Microsoft Defender ativo;
* mantenha o Isolamento do Núcleo;
* não altere todos os serviços;
* não desative a indexação sem necessidade;
* não desative hibernação em notebooks sem consultar o usuário.

### Etapa 7 — Aplicação

1. Revise tudo o que foi selecionado.
2. Desmarque qualquer opção que não esteja clara.
3. Execute o script como administrador.
4. Leia as mensagens apresentadas.
5. Não desligue o computador durante a execução.
6. Reinicie o Windows ao terminar.

---
<a name="procedimento-tecnicos"></a>
## 7. Procedimento recomendado para técnicos

Para uso profissional, aplique uma metodologia controlada.
<a name="levantamento-equipamento"></a>
### 7.1 Faça o levantamento do equipamento

Registre:

```text
Cliente:
Usuário:
Fabricante e modelo:
Número de série:
Versão do Windows:
Edição:
Versão da BIOS:
Processador:
Memória RAM:
Armazenamento:
Espaço disponível:
Placa de vídeo:
Aplicativos essenciais:
Recursos especiais:
Data da intervenção:
```
<a name="estabelecer-objetivo"></a>
### 7.2 Estabeleça o objetivo

Exemplos:

* reduzir aplicativos promocionais;
* preparar uma máquina nova;
* liberar espaço;
* padronizar computadores;
* otimizar uma estação de jogos;
* aumentar a privacidade;
* corrigir arquivos do sistema;
* automatizar a instalação de programas.

Não aplique o mesmo conjunto de alterações em todos os computadores.
<a name="perfis"></a>
### 7.3 Crie perfis diferentes

Uma assistência técnica pode manter perfis como:

#### Perfil básico

* limpeza;
* ponto de restauração;
* remoção de aplicativos promocionais;
* redução moderada de telemetria;
* instalação de aplicativos essenciais.

#### Perfil corporativo

* somente ajustes aprovados;
* preservação de recursos de gerenciamento;
* manutenção de telemetria exigida pela empresa;
* compatibilidade com domínio, VPN e Microsoft 365;
* registro de todas as mudanças.

#### Perfil para jogos

* remoção de gravação em segundo plano, quando autorizada;
* teste de HAGS;
* análise do plano de energia;
* manutenção dos componentes Xbox necessários;
* medição de FPS, latência e estabilidade.

#### Perfil para computador antigo

* remoção moderada de aplicativos;
* redução de programas em segundo plano;
* análise da indexação;
* verificação de saúde do disco;
* plano de energia adequado;
* manutenção da segurança.
<a name="exportar-configuracao"></a>
### 7.4 Exporte a configuração

Quando disponível, utilize o recurso de exportação do WinScript.

Salve com nomes claros:

```text
winscript-basico-windows11.json
winscript-jogos-desktop.json
winscript-notebook-empresa.json
```

Inclua também:

* versão da configuração;
* data;
* responsável;
* versão do Windows testada;
* alterações conhecidas;
* procedimento para reversão.

O projeto permite importar configurações por arquivo, inclusive por parâmetro na versão desktop.

Exemplo apresentado pelo projeto:

```powershell
winscript.exe -i "C:\caminho\config.json"
```
<a name="testes"></a>
### 7.5 Teste antes de implantar

Antes de usar o perfil em vários computadores:

1. teste em uma máquina não crítica;
2. reinicie várias vezes;
3. execute o Windows Update;
4. teste impressora e scanner;
5. teste câmera, áudio e microfone;
6. teste Bluetooth;
7. teste VPN;
8. teste compartilhamentos de rede;
9. teste aplicativos corporativos;
10. monitore o Visualizador de Eventos;
11. confirme que o Microsoft Defender continua ativo;
12. valide o desempenho com medições.

---

## 8. Como avaliar se houve melhoria

A sensação de velocidade pode ser enganosa. Sempre que possível, faça medições antes e depois.

## 8.1 Tempo de inicialização

Meça o tempo desde o acionamento do computador até o sistema estar pronto para uso.

Repita o teste pelo menos três vezes.

## 8.2 Uso de memória

Abra o **Gerenciador de Tarefas** e observe:

* memória usada após a inicialização;
* quantidade de processos;
* aplicativos em segundo plano;
* programas com alto consumo.

Espere alguns minutos após entrar no Windows antes de registrar os valores.

## 8.3 Uso de processador

Com o computador parado, observe se existem processos consumindo processador continuamente.

Um uso momentâneo pode ocorrer por:

* Windows Update;
* verificação do antivírus;
* indexação;
* sincronização;
* instalação de drivers;
* manutenção automática.

## 8.4 Uso do disco

Observe no Gerenciador de Tarefas:

* porcentagem de atividade;
* tempo de resposta;
* processos que mais acessam o disco;
* espaço disponível.

Uso constante de 100% pode indicar:

* disco rígido desgastado;
* pouca memória RAM;
* atualizações;
* antivírus;
* erros no sistema;
* falha física;
* programas problemáticos.

Nesses casos, somente um script de otimização pode não resolver a causa.

## 8.5 Temperatura

Em computadores com superaquecimento, o processador pode reduzir automaticamente a velocidade.

Verifique:

* poeira;
* ventoinhas;
* pasta térmica;
* circulação de ar;
* temperatura do processador e da placa de vídeo.

Ativar um plano de desempenho máximo em um computador superaquecendo pode piorar o problema.

## 8.6 Jogos

Para jogos, compare:

* média de FPS;
* FPS mínimo;
* tempo de quadro;
* travamentos;
* uso de CPU;
* uso de GPU;
* temperatura;
* estabilidade dos drivers.

Utilize sempre:

* o mesmo jogo;
* a mesma cena;
* a mesma resolução;
* as mesmas configurações gráficas;
* condições semelhantes.

---

## 9. O que o WinScript não consegue resolver

O WinScript pode ajudar na configuração do sistema, mas não corrige todos os tipos de lentidão.

Ele não substitui:

* troca de um disco rígido defeituoso;
* instalação de mais memória RAM;
* limpeza física;
* correção de superaquecimento;
* remoção especializada de malware;
* substituição de fonte defeituosa;
* reparo de placa-mãe;
* atualização de hardware muito antigo;
* reinstalação do Windows quando o sistema está severamente danificado.

### Exemplos

#### Computador com disco rígido antigo

A maior melhoria pode vir da troca por um SSD, e não da desativação de serviços.

#### Computador com pouca memória

Um sistema com pouca memória pode continuar lento mesmo após o debloat.

#### Computador infectado

A prioridade deve ser identificar e remover a ameaça. Não utilize otimização para esconder sintomas de malware.

#### Computador superaquecendo

É necessário resolver a refrigeração antes de ativar modos de alto desempenho.

---

## 10. Alterações que devem ser evitadas por usuários iniciantes

Não é recomendável selecionar, sem conhecimento técnico:

* remoção completa da Microsoft Store;
* remoção profunda do Microsoft Edge;
* remoção de todos os aplicativos;
* desativação do Microsoft Defender;
* desativação do firewall;
* desativação do Windows Update;
* desativação do Isolamento do Núcleo;
* alteração indiscriminada de serviços;
* desativação de componentes de rede;
* remoção do OneDrive sem verificar os arquivos;
* remoção de recursos de recuperação;
* modificações corporativas em computadores gerenciados.

> Quanto maior o número de alterações aplicadas ao mesmo tempo, mais difícil será descobrir qual delas causou um problema.

---

## 11. Como aplicar alterações com segurança

Use o princípio de alterações graduais:

1. Crie um ponto de restauração.
2. Selecione poucas opções.
3. Execute o script.
4. Reinicie o Windows.
5. Teste o computador.
6. Aguarde alguns dias, quando possível.
7. Aplique o próximo grupo de mudanças.

Uma divisão recomendada é:

```text
Grupo 1: limpeza e aplicativos promocionais
Grupo 2: privacidade
Grupo 3: telemetria
Grupo 4: desempenho
Grupo 5: jogos e personalizações
```

Essa abordagem torna a solução de problemas muito mais simples.

---

## 12. Como desfazer alterações

A forma de reversão depende da alteração realizada.

### 12.1 Usar a opção inversa no WinScript

Algumas configurações podem oferecer ações para ativar ou restaurar um recurso.

Abra novamente o WinScript, localize a opção e verifique se há uma configuração inversa.

### 12.2 Reinstalar um aplicativo

Aplicativos removidos podem ser reinstalados por:

* Microsoft Store;
* Winget;
* site oficial do desenvolvedor;
* pacote de instalação da empresa.

### 12.3 Usar a Restauração do Sistema

Para abrir a Restauração do Sistema:

1. Pressione `Windows + R`.
2. Digite:

```text
rstrui.exe
```

3. Pressione **Enter**.
4. Selecione o ponto criado antes do WinScript.
5. Examine os programas que serão afetados.
6. Confirme a restauração.

A Restauração do Sistema pode reverter arquivos do sistema, programas, configurações e alterações no Registro sem apagar os arquivos pessoais tradicionais. Programas e drivers instalados depois do ponto selecionado podem ser removidos.

### 12.4 Usar o Ambiente de Recuperação

Quando o Windows não inicia normalmente:

1. Entre no Ambiente de Recuperação do Windows.
2. Abra **Solução de Problemas**.
3. Entre em **Opções avançadas**.
4. Utilize **Restauração do Sistema** ou outra ferramenta adequada.

### 12.5 Restaurar backup ou reinstalar o Windows

Em casos graves, pode ser necessário:

* restaurar uma imagem do sistema;
* recuperar os arquivos de um backup;
* reparar o Windows;
* fazer uma reinstalação de reparo;
* reinstalar o sistema operacional.

---

## 13. Solução de problemas comuns

## 13.1 O WinScript não abre

Verifique:

* se o Windows está atualizado;
* se o aplicativo foi instalado corretamente;
* se o antivírus bloqueou o arquivo;
* se a arquitetura é compatível;
* se o aplicativo está sendo executado como administrador.

Baixe ou instale a ferramenta somente por uma fonte oficial.

## 13.2 O script apresenta acesso negado

Provavelmente ele não está sendo executado com privilégios administrativos.

Feche o terminal e abra:

* **PowerShell como administrador**; ou
* **Terminal como administrador**.

## 13.3 Um aplicativo desapareceu

O aplicativo pode ter sido removido pela categoria Debloat.

Procure o programa:

* na Microsoft Store;
* no Winget;
* no site oficial;
* no instalador corporativo.

## 13.4 A pesquisa ficou lenta

Verifique se a indexação do Windows Search foi desativada.

Reative o serviço ou restaure a configuração relacionada à indexação.

## 13.5 O notebook descarrega mais rápido

Verifique o plano de energia.

Troque **Ultimate Performance** ou **Alto Desempenho** pelo plano **Equilibrado**.

## 13.6 A impressora deixou de funcionar

Verifique se algum serviço de impressão foi desativado.

O serviço **Spooler de Impressão** deve estar disponível para a maioria das impressoras.

## 13.7 O Bluetooth deixou de funcionar

Algum serviço ou componente de Bluetooth pode ter sido desativado.

Restaure as configurações relacionadas e reinstale o driver fornecido pelo fabricante, se necessário.

## 13.8 A câmera ou o microfone não funcionam

Verifique:

1. as permissões de privacidade;
2. as configurações do aplicativo;
3. o driver;
4. as opções selecionadas no WinScript.

## 13.9 O OneDrive não sincroniza

Verifique se:

* o OneDrive foi removido;
* serviços de sincronização foram desativados;
* a conta Microsoft foi desconectada;
* permissões de rede foram alteradas.

## 13.10 O computador ficou instável

1. Pare de aplicar novas alterações.
2. Reinicie o computador.
3. Reverta as últimas opções.
4. Utilize o ponto de restauração.
5. Verifique o Visualizador de Eventos.
6. Teste memória, armazenamento e temperatura.
7. Confirme que o problema não é causado por hardware ou driver.

---

## 14. Modelo de configuração conservadora

O modelo abaixo é apenas uma referência. Os nomes exatos podem variar conforme a versão do WinScript.

```text
TOOLS
[X] Criar ponto de restauração
[X] Limpar arquivos temporários
[ ] Redefinir rede
[ ] Limpar histórico dos navegadores
[ ] Reparar o Windows, exceto quando necessário

DEBLOAT
[X] Remover aplicativos promocionais conhecidos
[X] Desativar sugestões e conteúdo de consumo
[X] Desativar Widgets, quando não utilizados
[ ] Remover Microsoft Store
[ ] Remover Microsoft Edge
[ ] Remover OneDrive sem verificar a sincronização
[ ] Remover todos os aplicativos

PRIVACY
[X] Desativar identificador de publicidade
[X] Reduzir sugestões personalizadas
[X] Limitar aplicativos desnecessários em segundo plano
[X] Revisar permissões de localização
[X] Revisar permissões de câmera e microfone
[ ] Bloquear globalmente recursos utilizados pelo usuário

TELEMETRY
[X] Reduzir coleta opcional
[X] Reduzir telemetria de aplicativos não utilizados
[ ] Desativar indiscriminadamente todos os serviços

PERFORMANCE
[X] Manter plano Equilibrado em notebooks
[X] Manter Microsoft Defender
[X] Manter Isolamento do Núcleo
[ ] Alterar todos os serviços para Manual
[ ] Desativar Windows Search sem necessidade
[ ] Desativar hibernação sem consultar o usuário
[ ] Ativar Ultimate Performance em qualquer computador
```

---

## 15. Modelo de checklist para técnicos

```text
[ ] Backup dos arquivos confirmado
[ ] Windows atualizado
[ ] Drivers atualizados
[ ] Estado de ativação registrado
[ ] Aplicativos essenciais registrados
[ ] Sincronização do OneDrive verificada
[ ] Ponto de restauração criado
[ ] Configuração do WinScript exportada
[ ] Script revisado
[ ] Alterações aplicadas como administrador
[ ] Computador reiniciado
[ ] Rede testada
[ ] Áudio testado
[ ] Câmera e microfone testados
[ ] Bluetooth testado
[ ] Impressora testada
[ ] Microsoft Defender verificado
[ ] Windows Update testado
[ ] Aplicativos do usuário testados
[ ] Desempenho antes e depois registrado
[ ] Procedimento documentado
```

---

## 16. Boas práticas de segurança

### Utilize somente fontes oficiais

Não baixe versões modificadas do WinScript de:

* fóruns;
* sites de downloads genéricos;
* links enviados por desconhecidos;
* vídeos com arquivos próprios;
* repositórios não relacionados ao projeto oficial.

### Revise o script

Quando possível, abra o script em um editor de texto antes de executá-lo.

Procure entender:

* quais aplicativos serão removidos;
* quais serviços serão modificados;
* quais chaves de Registro serão alteradas;
* quais comandos serão baixados;
* quais recursos de segurança serão afetados.

### Não execute como administrador sem necessidade

A execução administrativa é necessária para aplicar as alterações, mas aumenta o impacto de qualquer comando malicioso ou incorreto.

Confirme sempre:

* a origem;
* o endereço;
* o conteúdo;
* a finalidade do script.

### Não desative a segurança para obter ganhos mínimos

Não comprometa:

* antivírus;
* firewall;
* atualizações;
* criptografia;
* segurança baseada em virtualização;
* proteção contra ameaças;
* recuperação do sistema.

Pequenos ganhos de desempenho raramente justificam uma redução significativa da segurança.

---

## 17. Perguntas frequentes

### O WinScript é gratuito?

Sim. O projeto é gratuito, de código aberto e distribuído sob licença GPL-3.0. O código-fonte está disponível publicamente para consulta.

### Funciona no Windows 10?

O projeto informa suporte à criação de scripts para Windows 10 e Windows 11. Algumas opções podem existir somente em determinadas versões.

> O suporte regular gratuito do Windows 10 terminou em 14 de outubro de 2025. Computadores ainda executando esse sistema devem ter sua estratégia de segurança e atualização avaliada.

### É necessário executar como administrador?

Sim. A documentação oficial informa que privilégios administrativos são necessários para o funcionamento adequado das alterações.

### O WinScript aumenta o FPS?

Algumas alterações podem melhorar a estabilidade ou reduzir determinadas tarefas em segundo plano, mas não existe garantia de aumento de FPS.

O resultado depende do hardware, drivers, jogo e configuração.

### É seguro remover todos os aplicativos do Windows?

Não. A remoção ampla pode afetar aplicativos e recursos necessários. Remova apenas itens conhecidos.

### Posso usar em um computador de empresa?

Somente com autorização e após verificar as políticas da organização. Alterações de telemetria, serviços, segurança, atualização e autenticação podem interferir no gerenciamento corporativo.

### Devo desativar o Microsoft Defender?

Não. Para a maioria dos computadores, o Defender deve permanecer ativo e atualizado.

### Devo desativar a Integridade da Memória?

Para usuários comuns, não. Ela reforça a proteção do núcleo do Windows contra código malicioso. A desativação deve ser uma decisão técnica baseada em medições e avaliação de risco.

### Preciso marcar todas as opções?

Não. O principal benefício do WinScript é permitir uma configuração personalizada.

Marcar tudo geralmente aumenta o risco de:

* perder funcionalidades;
* criar incompatibilidades;
* reduzir a segurança;
* dificultar a solução de problemas.

### Posso executar o WinScript mais de uma vez?

Sim, mas revise novamente as opções e verifique se elas ainda são adequadas à versão atual do Windows e da ferramenta.

---

## 18. Conclusão

O WinScript pode ser útil para limpar, configurar, personalizar e otimizar o Windows, principalmente quando é utilizado de forma seletiva.

Os melhores resultados normalmente vêm de uma combinação de ações:

* remover somente aplicativos realmente desnecessários;
* reduzir programas iniciados automaticamente;
* manter o Windows e os drivers atualizados;
* liberar espaço em disco;
* revisar permissões de privacidade;
* preservar os recursos de segurança;
* corrigir problemas de hardware;
* medir o desempenho antes e depois.

A abordagem mais segura não é selecionar o maior número possível de opções. É selecionar apenas as mudanças adequadas para aquele computador e para a rotina de seu usuário.

Em resumo:

> **Crie um backup, gere um ponto de restauração, aplique poucas alterações de cada vez, preserve os recursos de segurança e teste o computador depois de cada etapa.**
