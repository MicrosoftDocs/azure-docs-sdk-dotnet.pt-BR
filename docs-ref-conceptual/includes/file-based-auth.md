Crie um arquivo de texto chamado `azureauth.json`. Cole o saída do JSON exibida quando criou a entidade de serviço.

Salve esse arquivo em um local seguro no sistema onde o seu código possa lê-lo. Use o PowerShell para definir uma variável de ambiente denominada `AZURE_AUTH_LOCATION` com o caminho completo para o arquivo, por exemplo:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
