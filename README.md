# Goof Troop Android — integração inicial do emulador

Este projeto Android em Java agora abre uma tela de jogo em paisagem, inclui a ROM `.smc` enviada nesta conversa e carrega o núcleo SNES do EmulatorJS por CDN. O EmulatorJS fornece os controles táteis na tela.

## Limitações importantes

- **Ainda não há APK compilado nem teste em aparelho.** Este ambiente não contém Android SDK nem Gradle, então não foi possível compilar e verificar o pacote aqui.
- A primeira execução e o jogo exigem internet, porque os arquivos do EmulatorJS/núcleo SNES são carregados de `https://cdn.emulatorjs.org/stable/data/`.
- A ROM fica empacotada em `app/src/main/assets/goof_troop.smc`.
- O projeto usa AndroidX WebKit para servir a ROM local por uma origem HTTPS segura dentro do WebView.
- Use a ROM somente se você tiver o direito de utilizá-la. Verifique as licenças e condições do emulador/núcleo antes de redistribuir o APK; este projeto não deve ser tratado como pronto para distribuição comercial.

## Compilar localmente

1. Instale Android Studio e Android SDK Platform 35.
2. Abra a pasta `goof_troop_android` no Android Studio.
3. Aguarde a sincronização do Gradle e aceite a instalação das dependências.
4. Selecione **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. O APK de depuração, se a compilação for bem-sucedida, estará em `app/build/outputs/apk/debug/app-debug.apk`.

## Compilar pelo GitHub Actions

O arquivo `.github/workflows/android.yml` permite compilar o APK em um runner do GitHub:

1. Envie o conteúdo desta pasta para um repositório GitHub seu.
2. Abra a aba **Actions** e execute **Build Android APK** (ou envie um commit para `main`/`master`).
3. Quando o workflow terminar com sucesso, baixe o artefato `Goof-Troop-Android-debug` na execução.

O workflow de CI é uma alternativa de compilação; não significa que o APK já tenha sido compilado ou testado.
