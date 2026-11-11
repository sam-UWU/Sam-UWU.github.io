# Chrōnos para Android

App Android do site Chrōnos. Ao abrir, a primeira tela (SplashActivity) é a tela de carregamento com o logo Chrōnos (fundo cinza claro e "Loading"). Depois abre o site dentro de um WebView, com o arquivo
`app/src/main/assets/index.html` embutido no app. Cadastro, login, catálogo e
avatar funcionam como no site, e o login fica salvo no aparelho.

## Como gerar o APK

1. Instale o **Android Studio** (https://developer.android.com/studio).
2. Abra o Android Studio, escolha **Open** e selecione a pasta `ChronosApp`.
3. Espere o **Gradle Sync** terminar (precisa de internet na primeira vez).
4. Menu **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
5. O arquivo fica em `app/build/outputs/apk/debug/app-debug.apk`.
6. Copie o APK para o celular e instale (ative "instalar apps desconhecidos").

Para testar direto: ligue o celular por cabo com a depuração USB ativa e aperte **Run**.

## Para atualizar o site dentro do app

Troque o arquivo `app/src/main/assets/index.html` pelo novo e gere o APK de novo.

## Notas

- As fontes do Google só carregam com internet. Sem internet, o app usa fontes do sistema.
- Para publicar na Play Store, gere um app assinado (**Build > Generate Signed Bundle**).

## Gerar o APK sem Android Studio (pelo celular, usando o GitHub)

1. Crie uma conta grátis em github.com e um repositório novo (qualquer nome).
2. No repositório: **Add file > Create new file**. No nome, digite `.github/workflows/build.yml`
   (as barras criam as pastas) e cole o conteúdo do arquivo `build.yml`. Confirme com **Commit**.
3. **Add file > Upload files** e envie o arquivo `chronos-android.zip`. Confirme com **Commit**.
4. Abra a aba **Actions**. O build roda sozinho e leva uns 5 a 10 minutos.
5. Quando ficar verde, abra a execução e baixe **chronos-apk** (é um zip com o `app-debug.apk`).
6. Extraia o zip, abra o `app-debug.apk` e instale (permita "instalar apps desconhecidos").

## Site público e sincronização (Firebase)

O site e o app usam o mesmo Firebase (projeto chronos-50e22): login, saldo em Sorbux,
itens comprados e itens equipados ficam salvos na nuvem e aparecem nos dois.
Para o site funcionar fora do Claude, publique o arquivo `index.html` no GitHub Pages:
repositório > Settings > Pages > Deploy from a branch > main / (root).
