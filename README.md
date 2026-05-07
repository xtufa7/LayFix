<p align="center">
  <img src="docs/images/layfix-icon.png" width="96" alt="LayFix logo">
</p>

<h1 align="center">LayFix</h1>

<p align="center">
  Instant keyboard layout fixer for Arabic and English mixed text.
</p>

<p align="center">
  <strong>v1.0.0 stable</strong> · Windows first · Linux core ready · Local only
</p>

---

## الفكرة

LayFix تطبيق خفيف يعيش في التراي ويصلح أخطاء تبديل الكيبورد بين العربي والإنجليزي.

حدد النص في أي تطبيق، اضغط الاختصار، وLayFix يستبدل النص المحدد فقط بالنسخة المصححة. لا يلمس أي نص خارج التحديد.

## صور توضيحية

### الأيقونة

<p align="center">
  <img src="docs/images/layfix-icon.png" width="160" alt="LayFix icon">
</p>

### مكان التطبيق في التراي

<p align="center">
  <img src="docs/images/tray-reference.png" width="720" alt="LayFix tray guide">
</p>

## أمثلة نظيفة

### عربي مكتوب على تخطيط إنجليزي

```text
hgsghl ugd;l
```

الناتج:

```text
السلام عليكم
```

### إنجليزي مكتوب على تخطيط عربي

```text
اثممخ LayFix
```

الناتج:

```text
hello LayFix
```

### نص مختلط

```text
pdh fhg; LayFix
```

الناتج:

```text
حيا بالك LayFix
```

## أهم الميزات

- يعمل من system tray فقط.
- لا تظهر نافذة رئيسية عند التشغيل العادي.
- يحول النص المحدد في مكانه.
- يحافظ على المسافات، الأسطر، وعلامات الترقيم قدر الإمكان.
- Clipboard Convert من قائمة التراي.
- Settings فيها الاختصارات، الثيم، التشغيل مع ويندوز، والتشخيص.
- History مغلق افتراضيًا للخصوصية.
- Startup with Windows مغلق افتراضيًا.
- يدعم Light و Dark و Follow system.
- Check for Updates يقارن الإصدار الحالي مع آخر GitHub Release.
- لا يوجد telemetry أو analytics أو رفع نصوص لأي مكان.

## طريقة الاستخدام

1. شغل LayFix.
2. ستجد الأيقونة في system tray.
3. حدد نصًا في أي تطبيق.
4. اضغط اختصار التحويل.
5. LayFix ينسخ النص المحدد، يحوله محليًا، ثم يلصقه مكان التحديد فقط.

الاختصار الافتراضي:

```text
Ctrl+Alt+F9
```

## قائمة التراي

```text
Settings
Clipboard Convert
About
Check for Updates
Exit
```

## الخصوصية

LayFix مصمم ليبقى محليًا.

- لا telemetry.
- لا analytics.
- لا cloud conversion.
- لا يتم رفع النص المحدد.
- لا يتم تخزين النصوص إلا إذا فعّل المستخدم History يدويًا.
- Diagnostics تعرض أطوال النصوص وحالة العملية فقط، وليس محتوى النص.

ملاحظة: زر `Check for Updates` يعمل فقط عند ضغط المستخدم عليه، ويتصل بـ GitHub Releases.

## كيف يعمل التحويل المحدد

LayFix يستخدم clipboard-first pipeline:

1. يحفظ محتوى الحافظة الحالي إذا أمكن.
2. يضع marker مؤقت وفريد في الحافظة.
3. يرسل `Ctrl+C` للتطبيق النشط.
4. ينتظر حتى تتغير الحافظة من marker إلى النص المحدد.
5. إذا لم يتم التقاط نص محدد، لا يحدث تحويل ولا لصق.
6. يحول النص محليًا.
7. يضع النص المحول في الحافظة.
8. يرسل `Ctrl+V` ليتم استبدال التحديد فقط.
9. يعيد محتوى الحافظة السابق بعد تأخير قصير.

## هيكل المشروع

```text
LayFix/
  README.md
  LayFix.sln

  docs/
    images/
      layfix-icon.png
      tray-reference.png

  src/
    LayFix.Core/
      KeyboardLayoutConverter.cs

    LayFix.Windows/
      App.xaml
      Services/
      Views/
      Assets/

    LayFix.Linux/
      Program.cs

  tests/
    LayFix.Core.Tests/
    LayFix.Windows.IntegrationTests/

  installer/
    LayFix.wxs

  artifacts/
    publish/
    installer/

  release/
    LayFix-portable.exe
    LayFix-installer.msi
    LayFix-linux-x64
    LayFix-release.zip
    README.md
```

## ترتيب ملفات الريليز

عند نشر إصدار جديد، خليه بهذا الشكل:

```text
release/
  LayFix-portable.exe
  LayFix-installer.msi
  LayFix-linux-x64
  LayFix-release.zip
  README.md
```

اسم GitHub tag:

```text
v1.0.0
```

عنوان الريليز المقترح:

```text
LayFix v1.0.0 Stable
```

وصف مختصر للريليز:

```text
First stable release of LayFix.

Includes:
- Windows tray-first app
- Portable EXE
- MSI installer
- Linux preview CLI
- Local Arabic/English layout conversion
```

Assets التي ترفعها في GitHub Release:

```text
LayFix-portable.exe
LayFix-installer.msi
LayFix-linux-x64
LayFix-release.zip
```

## متطلبات البناء

### Windows

- Windows 10 أو Windows 11
- .NET 8 SDK
- .NET 8 Desktop Runtime لتشغيل نسخة framework-dependent
- WiX Toolset CLI لبناء MSI

### Linux Preview

- .NET 8 Runtime
- اختياريًا:
  - `wl-paste` و `wl-copy` على Wayland
  - `xclip` على X11

## بناء المشروع

```powershell
dotnet restore LayFix.sln
dotnet build LayFix.sln -c Release
```

تشغيل نسخة ويندوز من السورس:

```powershell
dotnet run --project src\LayFix.Windows\LayFix.Windows.csproj -c Release
```

اختبار التحويل من CLI:

```powershell
.\release\LayFix-portable.exe --convert-text "hgsghl ugd;l"
```

الناتج المتوقع:

```text
السلام عليكم
```

## بناء Portable EXE

```powershell
dotnet publish src\LayFix.Windows\LayFix.Windows.csproj `
  -p:PublishProfile=portable-win-x64 `
  -o artifacts\publish\LayFix-win-x64
```

الملف الناتج:

```text
artifacts\publish\LayFix-win-x64\LayFix.exe
```

انسخه للريليز:

```powershell
Copy-Item artifacts\publish\LayFix-win-x64\LayFix.exe release\LayFix-portable.exe -Force
```

## بناء MSI Installer

ثبت WiX:

```powershell
dotnet tool install --global wix
```

ابنِ ملف MSI:

```powershell
wix build installer\LayFix.wxs `
  -d PublishDir="$PWD\artifacts\publish\LayFix-win-x64" `
  -o artifacts\installer\LayFix.msi
```

انسخه للريليز:

```powershell
Copy-Item artifacts\installer\LayFix.msi release\LayFix-installer.msi -Force
```

## بناء Linux Preview

```powershell
dotnet publish src\LayFix.Linux\LayFix.Linux.csproj `
  -c Release `
  -r linux-x64 `
  --self-contained false `
  -p:PublishSingleFile=true `
  -o artifacts\publish\LayFix-linux-x64
```

انسخه للريليز:

```powershell
Copy-Item artifacts\publish\LayFix-linux-x64\LayFix.Linux release\LayFix-linux-x64 -Force
```

## تجهيز ZIP للريليز

```powershell
Copy-Item README.md release\README.md -Force

Compress-Archive `
  -Path release\LayFix-portable.exe, `
        release\LayFix-installer.msi, `
        release\LayFix-linux-x64, `
        release\README.md `
  -DestinationPath release\LayFix-release.zip `
  -Force
```

## اختبارات قبل النشر

شغل اختبارات التحويل:

```powershell
dotnet run --project tests\LayFix.Core.Tests\LayFix.Core.Tests.csproj -c Release
```

شغل اختبار استبدال النص في WPF TextBox:

```powershell
dotnet run --project tests\LayFix.Windows.IntegrationTests\LayFix.Windows.IntegrationTests.csproj -c Release
```

اختبر ملف الريليز النهائي:

```powershell
.\release\LayFix-portable.exe --convert-text "pdh fhg; LayFix"
```

الناتج المتوقع:

```text
حيا بالك LayFix
```

## Check for Updates

LayFix يقارن الإصدار الحالي `v1.0.0 stable` مع آخر Release من:

```text
https://github.com/XTUFA7/LayFix/releases/latest
```

حتى يعمل الفحص بشكل صحيح، تأكد أن الريبو يحتوي Release منشور باسم tag مثل:

```text
v1.0.0
```

## حسابات 0xTuFa7

- X: [@0xtufa7](https://x.com/0xtufa7)
- GitHub: [XTUFA7](https://github.com/XTUFA7)
- Instagram: [_BB5BB](https://instagram.com/_BB5BB)

## License

Add your license here before publishing the repository publicly.
