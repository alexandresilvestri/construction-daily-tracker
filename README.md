# 🏗️ Construction Daily Tracker

> Uma solução moderna e completa para gestão de folha de pagamento na construção civil, desenvolvida com Kotlin Multiplatform e funcionando 100% offline

[![Kotlin](https://img.shields.io/badge/Kotlin-2.1.0-blue.svg)](https://kotlinlang.org)
[![Compose Multiplatform](https://img.shields.io/badge/Compose-1.9.0-green.svg)](https://www.jetbrains.com/lp/compose-multiplatform/)
[![Room](https://img.shields.io/badge/Room-2.6.1-orange.svg)](https://developer.android.com/training/data-storage/room)

---

## APK para download: [Link](https://drive.google.com/drive/folders/1PtZLVo6KCa1w9JP4mgLfaEJYqMlMlMFC?usp=sharing)

## 📖 Sobre o Projeto

Gerenciar a folha de pagamento na construção civil é complicado, especialmente quando você precisa cuidar de diversas obras e calcular dias trabalhados com precisão. O **Construction Daily Tracker** resolve esses desafios com uma solução local e offline.

Seja gerenciando uma pequena equipe ou supervisionando múltiplas obras, este app ajuda você a:

✅ Rastrear funcionários em diferentes obras e funções
✅ Registrar ajustes diários (horas extras, faltas, bonificações)
✅ Calcular automaticamente a folha de pagamento com precisão
✅ Gerar relatórios mensais do dia 6 ao dia 5
✅ Manter um histórico completo de todas as alterações
✅ **Funcionar 100% offline - todos os dados ficam no seu celular**

---

## 🌟 Funcionalidades Principais

### 🎯 Cálculo Inteligente de Folha
- **Cálculo automático de dias úteis** excluindo finais de semana
- **Ajustes dinâmicos** para horas extras, faltas e bonificações
- **Atualizações em tempo real** quando ajustes são adicionados ou removidos
- **Precisão financeira** com BigDecimal para valores monetários

### 📱 Aplicativo Local e Offline
- **Banco de dados local** com Room/SQLite
- **Sem necessidade de internet** - funciona completamente offline
- **Dados seguros** armazenados no dispositivo
- **Interface moderna** construída com Compose Multiplatform
- **Lógica de negócio compartilhada** entre plataformas

### 🔐 Seguro & Privado
- **Dados locais** - tudo fica no seu dispositivo
- **Armazenamento criptografado** para preferências sensíveis
- **Sem envio de dados** para servidores externos
- **Cobertura de testes** seguindo princípios TDD

### 🏗️ Gestão Multi-Obras
- Rastreie múltiplas obras simultaneamente
- Atribua funcionários a diferentes funções
- Monitore trabalho em vários projetos
- Gere relatórios específicos por obra

---

## 🚀 Início Rápido

### Pré-requisitos

- **Android Studio** (versão mais recente)
- **JDK 11** ou superior
- **Dispositivo Android** ou emulador (API 24+)

### 📱 Instalar o App

#### Opção 1: Baixar APK Pré-compilado
1. Navegue até `composeApp/build/outputs/apk/debug/`
2. Transfira `composeApp-debug.apk` para seu dispositivo
3. Habilite "Instalar de fontes desconhecidas" nas configurações
4. Instale o APK

#### Opção 2: Compilar do Código-Fonte

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/construction-daily-tracker/
cd construction-daily-tracker

# Compile o APK de debug
./gradlew :composeApp:assembleDebug

# APK estará em: composeApp/build/outputs/apk/debug/composeApp-debug.apk

# Instalar via ADB (opcional)
adb install composeApp/build/outputs/apk/debug/composeApp-debug.apk
```

### 🧪 Executar Testes

```bash
# Executar todos os testes
./gradlew test

# Executar apenas testes do shared
./gradlew :shared:test

# Executar com saída detalhada
./gradlew test --info
```

---

## 🏛️ Arquitetura

Este projeto segue uma **arquitetura limpa e modular** com armazenamento local:

```
construction-daily-tracker/
├── shared/              # Lógica de negócio agnóstica de plataforma
│   ├── models/          # Modelos de dados (@Serializable)
│   └── utils/           # WorkDaysCalculator, helpers
└── composeApp/          # Aplicativo Android
    ├── commonMain/      # Código de UI compartilhado
    └── androidMain/     # Código específico do Android
        ├── database/    # Room database (entities, DAOs)
        ├── repository/  # Repositórios locais
        └── ui/          # Telas e componentes
```

### Stack Tecnológica

**Android:**
- **Compose Multiplatform** - UI declarativa moderna
- **Room Database** - Persistência local type-safe
- **SQLite** - Banco de dados embarcado
- **Kotlin Coroutines** - Operações assíncronas
- **ViewModel** - Gerenciamento de estado
- **EncryptedSharedPreferences** - Armazenamento seguro de preferências

**Compartilhado:**
- **Kotlin Serialization** - Serialização de dados
- **Kotlin Multiplatform** - Compartilhamento de código
