# 🎨 Guia de Integração do Logo - Grupo Impacto

## 📱 Como Adicionar o Logo do Grupo Impacto ao Projeto Android

### 1. Preparar o Logo

Salve o arquivo de logo do Grupo Impacto como `ic_logo_impacto.png` em diferentes resoluções:

#### Estrutura de Pastas de Recursos (drawable)

```
app/src/main/res/
├── drawable-ldpi/
│   └── ic_logo_impacto.png (36x36 dp)
├── drawable-mdpi/
│   └── ic_logo_impacto.png (48x48 dp)
├── drawable-hdpi/
│   └── ic_logo_impacto.png (72x72 dp)
├── drawable-xhdpi/
│   └── ic_logo_impacto.png (96x96 dp)
├── drawable-xxhdpi/
│   └── ic_logo_impacto.png (144x144 dp)
├── drawable-xxxhdpi/
│   └── ic_logo_impacto.png (192x192 dp)
└── drawable/
    └── ic_logo_impacto.png (versão padrão)
```

### 2. Adicionar Logo como Ícone do Aplicativo

#### Mínimo necessário para launcher icon:

```
app/src/main/res/mipmap-ldpi/
├── ic_launcher.png (36x36)
├── ic_launcher_round.png (36x36)

app/src/main/res/mipmap-mdpi/
├── ic_launcher.png (48x48)
├── ic_launcher_round.png (48x48)

app/src/main/res/mipmap-hdpi/
├── ic_launcher.png (72x72)
├── ic_launcher_round.png (72x72)

app/src/main/res/mipmap-xhdpi/
├── ic_launcher.png (96x96)
├── ic_launcher_round.png (96x96)

app/src/main/res/mipmap-xxhdpi/
├── ic_launcher.png (144x144)
├── ic_launcher_round.png (144x144)

app/src/main/res/mipmap-xxxhdpi/
├── ic_launcher.png (192x192)
├── ic_launcher_round.png (192x192)
```

### 3. Atualizar AndroidManifest.xml

```xml
<application
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    ...>
</application>
```

### 4. Adicionar Logo na Activity Principal

#### No activity_main.xml, o ImageView já está preparado:

```xml
<ImageView
    android:layout_width="80dp"
    android:layout_height="80dp"
    android:src="@drawable/ic_logo_impacto"
    android:contentDescription="App Icon"
    android:scaleType="centerInside" />
```

### 5. Criar Arquivo de Cor de Fundo (Opcional)

Você pode criar um arquivo `ic_background_impacto.xml` em `res/drawable/`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape xmlns:android="http://schemas.android.com/apk/res/android">
    <gradient
        android:type="linear"
        android:angle="135"
        android:startColor="#f5941e"
        android:endColor="#d97c2e" />
</shape>
```

### 6. Adicionar Splash Screen com Logo (Android 12+)

Crie um arquivo `splash_screen.xml` em `res/drawable/`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- Background -->
    <item>
        <shape>
            <solid android:color="#f5941e" />
        </shape>
    </item>
    
    <!-- Logo no Centro -->
    <item
        android:drawable="@drawable/ic_logo_impacto"
        android:gravity="center" />
</layer-list>
```

### 7. Usar Splash Screen em styles.xml

```xml
<style name="Theme.ChecklistSupervision.Splash">
    <item name="android:windowBackground">@drawable/splash_screen</item>
    <item name="android:windowNoTitle">true</item>
    <item name="android:windowFullscreen">true</item>
</style>
```

### 8. Atualizar MainActivity para usar Splash

```xml
<activity
    android:name=".ui.MainActivity"
    android:theme="@style/Theme.ChecklistSupervision.Splash"
    android:exported="true">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

E no código Java/Kotlin:

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    // Remove splash theme
    setTheme(R.style.Theme_ChecklistSupervision)
    super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
    
    // Rest of code...
}
```

## 📐 Dimensões Recomendadas

| Tipo | Dimensão | DPI |
|------|----------|-----|
| ldpi | 36x36 | 120 |
| mdpi | 48x48 | 160 |
| hdpi | 72x72 | 240 |
| xhdpi | 96x96 | 320 |
| xxhdpi | 144x144 | 480 |
| xxxhdpi | 192x192 | 640 |

## 🎨 Paleta de Cores - Grupo Impacto

```
Primária: #f5941e (Laranja)
Escura: #d97c2e (Laranja Escuro)
Secundária: #8b5a2b (Marrom)
```

## 📱 Integração com Material Design 3

Se estiver usando Material Design 3, atualize `styles.xml`:

```xml
<style name="Theme.ChecklistSupervision" parent="Theme.Material3.Light">
    <item name="colorPrimary">@color/primary</item>
    <item name="colorPrimaryContainer">@color/primary</item>
    <item name="colorSecondary">@color/secondary</item>
    <item name="colorSecondaryContainer">@color/secondary</item>
    <item name="colorTertiary">@color/accent</item>
    <item name="colorError">@color/error</item>
</style>
```

## 🔧 Ferramenta Útil: Android Asset Studio

Use a ferramenta online para gerar ícones rapidamente:
https://romannurik.github.io/AndroidAssetStudio/

## ✅ Checklist de Implementação

- [ ] Logo em 6 resoluções (ldpi até xxxhdpi)
- [ ] Ícone launcher em mipmap
- [ ] Ícone launcher redondo em mipmap_round
- [ ] Cores atualizadas em colors.xml
- [ ] Splash screen configurada
- [ ] MainActivity atualiza theme após splash
- [ ] Logo aparece na tela principal
- [ ] Strings.xml com branding Grupo Impacto
- [ ] App name contém "Grupo Impacto"

## 📝 Exemplo Completo de Integração

### colors.xml (já atualizado)
```xml
<color name="primary">#f5941e</color>
<color name="primary_dark">#d97c2e</color>
<color name="secondary">#8b5a2b</color>
```

### strings.xml (já atualizado)
```xml
<string name="app_name">Checklist Supervisão - Grupo Impacto</string>
<string name="brand_name">GRUPO IMPACTO - Serviços Terceirizados</string>
```

### activity_main.xml (logo já integrado)
```xml
<ImageView
    android:layout_width="80dp"
    android:layout_height="80dp"
    android:src="@drawable/ic_logo_impacto"
    android:contentDescription="Logo Grupo Impacto" />
```

## 🚀 Próximas Etapas

1. Copie o logo para as pastas drawable
2. Recompile o projeto
3. Execute o app para verificar se o logo aparece
4. Teste em diferentes tamanhos de tela

## 💡 Dicas

- Use formatos PNG com fundo transparente
- Mantenha proporções 1:1 para ícones
- Teste o logo em fundo claro e escuro
- Considere adicionar material de marca em documentação

## 📞 Suporte

Se tiver dúvidas sobre tamanhos ou formatos, consulte:
- [Documentação Oficial Android](https://developer.android.com/guide/practices/ui_guidelines/icon_design)
- [Material Design Guidelines](https://material.io/design/iconography/system-icons.html)

---

**Status**: ✅ Todos os arquivos já foram atualizados com o branding do Grupo Impacto!