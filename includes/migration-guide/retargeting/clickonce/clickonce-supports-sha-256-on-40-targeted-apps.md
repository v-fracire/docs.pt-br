### <a name="clickonce-supports-sha-256-on-40-targeted-apps"></a>ClickOnce é compatível com SHA-256 em aplicativos destinados ao 4.0

|   |   |
|---|---|
|Detalhes|Anteriormente, um aplicativo ClickOnce com um certificado assinado com SHA-256 exigia a presença do .NET Framework 4.5 ou posterior, mesmo se o aplicativo fosse direcionado ao 4.0. Agora, os aplicativos ClickOnce direcionados ao .NET Framework 4.0 podem ser executados no .NET Framework 4.0, mesmo quando assinados com SHA-256.|
|Sugestão|Essa alteração elimina essa dependência e permite que certificados SHA-256 sejam usados para assinar aplicativos ClickOnce destinados ao .NET Framework 4 e versões anteriores.|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Redirecionando|

