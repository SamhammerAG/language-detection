# Language Detection

.NET Port of [Language Detection Library for Java](https://code.google.com/p/language-detection/) by [@shuyo](https://github.com/shuyo)

## Compatibility

.NET Framework 4.6.1
.NET Standard 2.0

## Install

Add a reference to `LanguageDetection.dll`.

## Use

```csharp
using LanguageDetection;
```
    
Load all supported languages
    
```csharp
LanguageDetector detector = new LanguageDetector();
detector.AddAllLanguages();
Assert.AreEqual("lav", detector.Detect("čau, man iet labi, un kā iet tev?"));
```
    
or a small subset

```csharp
LanguageDetector detector = new LanguageDetector();
detector.AddLanguages("lav", "lit", "eng");
Assert.AreEqual("lav", detector.Detect("čau, man iet labi, un kā iet tev?"));
```

You can also change parameters

```csharp
LanguageDetector detector = new LanguageDetector();
detector.RandomSeed = 1;
detector.ConvergenceThreshold = 0.9;
detector.MaxIterations = 50;
```
    
## License

Apache 2.0


## How to publish package
- set package version in LanguageDetection.csproj
- create git tag
- dotnet pack -c Release
- nuget push .\bin\Release\LanguageDetection.*.nupkg NUGET_API_KEY -src https://api.nuget.org/v3/index.json
- (optional) nuget setapikey NUGET_API_KEY -source https://api.nuget.org/v3/index.json
