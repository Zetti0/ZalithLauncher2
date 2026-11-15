# MoonLauncher — fork comunitário
![Downloads](https://img.shields.io/github/downloads/Zetti0/ZalithLauncher2/total)
[![Sponsor](https://img.shields.io/badge/sponsor-30363D?logo=GitHub-Sponsors)](https://afdian.com/a/MovTery)

[Português (Brasil)](README.md) | [English](README_EN_US.md) | [繁體中文](README_ZH_TW.md)

> [!IMPORTANT]
> Este repositório é um fork comunitário do [ZalithLauncher2 oficial](https://github.com/ZalithLauncher/ZalithLauncher2). As alterações e builds publicados por `Zetti0` aqui são independentes e não são releases oficiais do projeto original.

O **MoonLauncher** é um launcher para Android voltado ao **Minecraft: Java Edition**. O projeto usa o [PojavLauncher](https://github.com/PojavLauncherTeam/PojavLauncher/tree/v3_openjdk/app_pojavlauncher/src/main/jni) como base de execução e constrói a interface com **Jetpack Compose** e **Material Design 3**. Ele é um projeto separado do [ZalithLauncher original](https://github.com/ZalithLauncher/ZalithLauncher).

O repositório upstream informa que o site `zalithlauncher.cn` está em desenvolvimento e alerta sobre sites de terceiros que usam o nome Zalith Launcher sem autorização. Confira sempre o domínio e evite inserir credenciais em sites que não sejam os oficiais dos serviços que você usa.

## Identidade e build de teste

O nome do app passa a ser **MoonLauncher**, com identificador Android próprio (`com.moonlauncher.launcher`) para poder coexistir com o launcher original. A tela inicial identifica o app como fork comunitário não oficial.

O fork inclui um layout de controles touch inspirado nos controles do Bedrock e uma opção de conta Offline. A conta Offline não autentica na Microsoft e só funciona em mundos/servidores que aceitam jogadores offline; servidores que exigem autenticação oficial não aceitam esse tipo de conta.

O APK Debug ARM64 para aparelhos como o Galaxy S23 com Snapdragon já está publicado em [Releases](https://github.com/Zetti0/ZalithLauncher2/releases/tag/moonlauncher-2.8.2-arm64-debug). É uma build de teste; a build Release assinada depende da nova keystore e dos secrets do GitHub Actions.

## Traduções

O projeto upstream usa o [Weblate](https://hosted.weblate.org/projects/zalithlauncher2) para organizar traduções. Contribuições de tradução são bem-vindas.

## Compilar o projeto

### Requisitos

- Android Studio recente
- Android SDK; API mínima 26
- JDK 21

### Build Debug

```bash
git clone https://github.com/Zetti0/ZalithLauncher2.git
cd ZalithLauncher2
./gradlew ZalithLauncher:assembleDebug -Darch=arm64
```

O parâmetro `arch` aceita `all`, `arm`, `arm64`, `x86` e `x86_64`. Os builds são feitos no GitHub Actions.

### Configurar assinatura Release

Gere uma keystore própria fora do repositório; mantenha uma cópia de backup em local seguro e não a envie ao GitHub como arquivo público. Use o alias `moonlauncher`:

```bash
keytool -genkeypair -v -keystore moonlauncher.jks -storetype JKS -alias moonlauncher -keyalg RSA -keysize 4096 -validity 10000
base64 -w0 moonlauncher.jks
```

No repositório GitHub, configure os secrets `KEYSTORE_BASE64` (resultado do comando base64), `STORE_PASSWORD` e `KEY_PASSWORD`. O workflow restaura a keystore somente durante o build Release. O app Debug continua usando a keystore Debug separada.

## Licença

O código é distribuído sob a [licença GPL-3.0](LICENSE).

### Termos adicionais publicados pelo projeto upstream (seção 7 da GPLv3)

1. Ao distribuir uma versão modificada, o upstream exige alterar o nome ou a versão para diferenciá-la da original. As cláusulas adicionais também dizem que o nome da versão modificada não deve conter “ZalithLauncher” nem “ZL”, e que a tela inicial ou principal deve identificá-la claramente como uma versão modificada não oficial. Consulte [GPLv3, seção 7(c)](https://github.com/ZalithLauncher/ZalithLauncher2/blob/969827b/LICENSE#L372-L374). O nome do app pode ser configurado em [gradle.properties](./ZalithLauncher/gradle.properties).
2. Os avisos de copyright exibidos pelo programa não devem ser removidos, conforme [GPLv3, seção 7(b)](https://github.com/ZalithLauncher/ZalithLauncher2/blob/969827b/LICENSE#L368-L370).

## Bibliotecas de código aberto e licenças

Este software utiliza as bibliotecas de código aberto listadas abaixo:

| Biblioteca                               | Direitos autorais                                                                                                     | Licença              | Link oficial                                                                      |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------|----------------------|------------------------------------------------------------------------------------|
| androidx-appcompat                    | Copyright © The Android Open Source Project                                                                   | Apache 2.0           | [Link↗](https://developer.android.com/jetpack/androidx/releases/appcompat)         |
| androidx-constraintlayout-compose     | Copyright © The Android Open Source Project                                                                   | Apache 2.0           | [Link↗](https://developer.android.com/develop/ui/compose/layouts/constraintlayout) |
| androidx-webkit                       | Copyright © The Android Open Source Project                                                                   | Apache 2.0           | [Link↗](https://developer.android.com/jetpack/androidx/releases/webkit)            |
| ANGLE                                 | Copyright 2018 The ANGLE Project Authors                                                                      | BSD 3-Clause License | [Link↗](http://angleproject.org/)                                                  |
| Apache Commons Codec                  | -                                                                                                             | Apache 2.0           | [Link↗](https://commons.apache.org/proper/commons-codec)                           |
| Apache Commons Compress               | -                                                                                                             | Apache 2.0           | [Link↗](https://commons.apache.org/proper/commons-compress)                        |
| Apache Commons IO                     | -                                                                                                             | Apache 2.0           | [Link↗](https://commons.apache.org/proper/commons-io)                              |
| ByteHook                              | Copyright © 2020-2024 ByteDance, Inc.                                                                         | MIT License          | [Link↗](https://github.com/bytedance/bhook)                                        |
| BuildKeys                             | Copyright © 2026 MovTery                                                                                      | Apache 2.0           | [Link↗](https://github.com/MovTery/BuildKeys)                                      |
| Coil Compose                          | Copyright © 2025 Coil Contributors                                                                            | Apache 2.0           | [Link↗](https://github.com/coil-kt/coil)                                           |
| Coil Gifs                             | Copyright © 2025 Coil Contributors                                                                            | Apache 2.0           | [Link↗](https://github.com/coil-kt/coil)                                           |
| Coil SVG                              | Copyright © 2025 Coil Contributors                                                                            | Apache 2.0           | [Link↗](https://github.com/coil-kt/coil)                                           |
| Fishnet                               | Copyright © 2025 Kyant                                                                                        | Apache 2.0           | [Link↗](https://github.com/Kyant0/Fishnet)                                         |
| gl4es_extra_extra                     | Copyright © 2016-2018 Sebastien Chevalier; Copyright (c) 2013-2016 Ryan Hileman                               | MIT License          | [Link↗](https://github.com/PojavLauncherTeam/gl4es_extra_extra)                    |
| Gson                                  | Copyright © 2008 Google Inc.                                                                                  | Apache 2.0           | [Link↗](https://github.com/google/gson)                                            |
| kotlinx.coroutines                    | Copyright © 2000-2020 JetBrains s.r.o.                                                                        | Apache 2.0           | [Link↗](https://github.com/Kotlin/kotlinx.coroutines)                              |
| ktor-client-content-negotiation       | Copyright © 2000-2023 JetBrains s.r.o.                                                                        | Apache 2.0           | [Link↗](https://ktor.io)                                                           |
| ktor-client-core                      | Copyright © 2000-2023 JetBrains s.r.o.                                                                        | Apache 2.0           | [Link↗](https://ktor.io)                                                           |
| ktor-client-okhttp                    | Copyright © 2000-2023 JetBrains s.r.o.                                                                        | Apache 2.0           | [Link↗](https://ktor.io)                                                           |
| ktor-http                             | Copyright © 2000-2023 JetBrains s.r.o.                                                                        | Apache 2.0           | [Link↗](https://ktor.io)                                                           |
| ktor-serialization-kotlinx-json       | Copyright © 2000-2023 JetBrains s.r.o.                                                                        | Apache 2.0           | [Link↗](https://ktor.io)                                                           |
| LWJGL - Lightweight Java Game Library | Copyright © 2012-present Lightweight Java Game Library All rights reserved.                                   | BSD 3-Clause License | [Link↗](https://github.com/LWJGL/lwjgl3)                                           |
| material-color-utilities              | Copyright 2021 Google LLC                                                                                     | Apache 2.0           | [Link↗](https://github.com/material-foundation/material-color-utilities)           |
| Maven Artifact                        | Copyright © The Apache Software Foundation                                                                    | Apache 2.0           | [Link↗](https://github.com/apache/maven/tree/maven-3.9.9/maven-artifact)           |
| Media3                                | Copyright © The Android Open Source Project                                                                   | Apache 2.0           | [Link↗](https://developer.android.com/jetpack/androidx/releases/media3)            |
| Mesa                                  | Copyright © The Mesa Authors                                                                                  | MIT License          | [Link↗](https://mesa3d.org/)                                                       |
| MobileGlues                           | Copyright © 2025-2026 MobileGL-Dev                                                                           | LGPL-2.1 License     | [Link↗](https://github.com/MobileGL-Dev/MobileGlues)                             |
| MMKV                                  | Copyright © 2018 THL A29 Limited, a Tencent company.                                                          | BSD 3-Clause License | [Link↗](https://github.com/Tencent/MMKV)                                           |
| Navigation 3                          | Copyright © The Android Open Source Project                                                                   | Apache 2.0           | [Link↗](https://developer.android.com/jetpack/androidx/releases/navigation3)       |
| NG-GL4ES                              | Copyright © 2016-2018 Sebastien Chevalier; Copyright © 2013-2016 Ryan Hileman; Copyright (c) 2025-2026 BZLZHH | MIT License          | [Link↗](https://github.com/BZLZHH/NG-GL4ES)                                        |
| OkHttp                                | Copyright © 2019 Square, Inc.                                                                                 | Apache 2.0           | [Link↗](https://github.com/square/okhttp)                                          |
| Okio                                  | Copyright © 2013 Square, Inc.                                                                                 | Apache 2.0           | [Link↗](https://square.github.io/okio/)                                            |
| OpenNBT                               | Copyright © 2013-2021 Steveice10.                                                                             | MIT License          | [Link↗](https://github.com/GeyserMC/OpenNBT)                                       |
| Process Phoenix                       | Copyright © 2015 Jake Wharton                                                                                 | Apache 2.0           | [Link↗](https://github.com/JakeWharton/ProcessPhoenix)                             |
| proxy-client-android                  | -                                                                                                             | LGPL-3.0 License     | [Link↗](https://github.com/TouchController/TouchController)                        |
| Reorderable                           | Copyright © 2023 Calvin Liang                                                                                 | Apache 2.0           | [Link↗](https://github.com/Calvin-LL/Reorderable)                                  |
| sdl2-compat                           | Copyright (C) 2026 Sam Lantinga <slouken@libsdl.org>                                                          | Zlib License         | [Link↗](https://github.com/libsdl-org/sdl2-compat)                                 |
| SDL3                                  | Copyright (C) 1997-2026 Sam Lantinga <slouken@libsdl.org>                                                     | Zlib License         | [Link↗](https://github.com/libsdl-org/SDL)                                         |
| SimpleFPEWrapper                      | Copyright © 2026 MobileGL-Dev                                                                                | LGPL-3.0 License     | [Link↗](https://github.com/MobileGL-Dev/SimpleFPEWrapper)                        |
| sora-editor                           | Copyright (C) 2020-2026  Rosemoe                                                                              | LGPL-2.1 License     | [Link↗](https://github.com/Rosemoe/sora-editor)                                    |
| StringFog                             | Copyright © 2016-2023, Megatron King                                                                          | Apache 2.0           | [Link↗](https://github.com/MegatronKing/StringFog)                                 |
| tm4e (TextMate for Eclipse)           | Copyright © Eclipse Foundation                                                                                | EPL-2.0 License      | [Link↗](https://github.com/eclipse-tm4e/tm4e)                                      |
| XZ for Java                           | Copyright © The XZ for Java authors and contributors                                                          | 0BSD License         | [Link↗](https://tukaani.org/xz/java.html)                                          |
