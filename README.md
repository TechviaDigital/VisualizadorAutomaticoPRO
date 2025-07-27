# Visualizador Automático PRO

O Visualizador Automático PRO é uma ferramenta de desktop para Windows, desenvolvida em Python com PyQt5, para facilitar o gerenciamento e interação com múltiplos dispositivos Android. Ele permite espelhar a tela, instalar APKs, reiniciar, capturar tela e muito mais, conectando-se aos dispositivos via cabo USB ou Wi-Fi (usando endereço IP).

O aplicativo agora é **portátil**, incluindo as ferramentas ADB e Scrcpy diretamente na pasta `vendor`, eliminando a necessidade de instalações manuais pelo usuário.

⚠️ **Aviso Importante sobre Antivírus (Windows Defender)**
Ao executar o aplicativo ou o scrcpy pela primeira vez, o Firewall do Windows Defender pode exibir um alerta de segurança sobre o `adb.exe`.

Isso é normal e esperado. O ADB é uma ferramenta de desenvolvedor que permite a comunicação entre o PC e o Android. O firewall detecta essa comunicação e pede sua permissão.

**É essencial que você clique em "Permitir acesso".** Se você bloquear, o aplicativo não conseguirá detectar ou controlar nenhum dos seus dispositivos.

## Funcionalidades Principais

*   **Detecção Automática de Dispositivos:** Lista automaticamente os dispositivos Android conectados com depuração USB ativa.
*   **Conexão via IP:** Permite conectar-se a dispositivos (como TV Box) na mesma rede local usando o endereço IP.
*   **Ações Individuais e em Lote (Modo Pro):**
    *   🖥️ **Espelhar Tela:** Inicia o `scrcpy` para os dispositivos selecionados.
    *   📦 **Instalar APK:** Instala um arquivo `.apk` em um ou múltiplos dispositivos.
    *   ♻️ **Reiniciar Dispositivo:** Envia um comando de reinicialização.
    *   📸 **Capturar Tela:** Tira screenshots e permite salvá-los no PC.
    *   🎬 **Gravar Tela:** Grava a sessão de espelhamento em um arquivo de vídeo.
    *   ℹ️ **Mostrar Informações:** Exibe detalhes do dispositivo (modelo, versão do Android, etc.).
*   **Página de Perfil e Configurações:**
    *   Acessível para todos os usuários (Free e Pro).
    *   Exibe os detalhes da sua licença.
    *   Centraliza as **Configurações de Aparência** (Temas e Cores) e **Configurações de Espelhamento** (Resolução e Bitrate).
*   **Modo Pro:** Ativado por uma chave de licença (validada online) para desbloquear funcionalidades avançadas como ações em lote.

## Instalação e Uso

O aplicativo foi projetado para ser o mais simples possível.

1.  **Baixe o executável (`.exe`)** da seção de [Releases do GitHub](https://github.com/TechviaDigital/VisualizadorAutomaticoPRO/releases).
2.  Coloque o `.exe` em uma pasta de sua preferência.
3.  Execute o arquivo. Tudo o que você precisa (ADB e Scrcpy) já está incluído.

## Como Usar

1.  **Conecte seus Dispositivos Android:**
    *   **Via USB:** Conecte um ou mais celulares/tablets. Ative as **Opções do Desenvolvedor** e habilite a **Depuração USB**.
    *   **Via Wi-Fi/Rede:**
        1.  No seu dispositivo Android, encontre o endereço IP local (geralmente em Configurações > Sobre > Status).
        2.  No Visualizador Automático PRO, clique em **"📡 Conectar via IP"** e insira o endereço.
        3.  (Pode ser necessário ativar a depuração ADB via Wi-Fi nas Opções do Desenvolvedor do seu dispositivo).
2.  **Execute o Aplicativo:**
    *   A interface principal mostrará os dispositivos detectados.
    *   Use os botões para interagir com um ou mais dispositivos.
    *   Acesse a página **"👤 Meu Perfil e Configs"** para alterar temas, cores e qualidade de espelhamento.

## Como Construir a Partir do Código-Fonte

Se você deseja modificar o aplicativo, siga estes passos:

1.  **Clone o Repositório:**
    ```bash
    git clone https://github.com/TechviaDigital/VisualizadorAutomaticoPRO.git
    cd VisualizadorAutomaticoPRO
    ```
2.  **Instale as Dependências Python:**
    ```bash
    pip install PyQt5 requests pyjwt
    ```
3.  **Obtenha as Dependências `vendor`:**
    *   Crie a pasta `vendor`.
    *   Baixe o [SDK Platform-Tools for Windows](https://developer.android.com/tools/releases/platform-tools) e copie `adb.exe`, `AdbWinApi.dll`, e `AdbWinUsbApi.dll` para uma subpasta `vendor/adb`.
    *   Baixe a última versão do [Scrcpy](https://github.com/Genymobile/scrcpy/releases) e copie seu conteúdo para uma subpasta `vendor/scrcpy`.
4.  **Execute o Script:**
    ```bash
    python visualizador_automatico_pro.py
    ```

### Empacotando em um `.exe`

1.  **Instale o PyInstaller:**
    ```bash
    pip install pyinstaller
    ```
2.  **Execute o Comando PyInstaller:**
    Abra um terminal na pasta do projeto e execute:
    ```bash
    pyinstaller --onefile --noconsole --icon=icone.ico --add-data "vendor;vendor" --add-data "logo.jpg;." --add-data "icons;icons" visualizador_automatico_pro.py
    ```
3.  O executável final estará na pasta `dist`.
