# .NET 10.0 Desktop Runtime (v10.0.5) - Windows x64 Installer

## Método 1: Permissão de admin
Baixar via: https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-10.0.5-windows-x64-installer

## Método 2: Sem permissão de admin

## 1) Abra o PowerShell
Pode ser o PowerShell normal mesmo, sem “Executar como administrador”.

## 2) Crie uma pasta local para o .NET
Rode:

```sh
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\dotnet"
```

## 3) Baixe o script oficial da Microsoft
Rode:

```sh
Invoke-WebRequest https://dot.net/v1/dotnet-install.ps1 -OutFile "$env:USERPROFILE\Downloads\dotnet-install.ps1"
```

## 4) Execute o script instalando o .NET 10 na sua pasta de usuário
Rode:

```sh
& "$env:USERPROFILE\Downloads\dotnet-install.ps1" -Channel 10.0 -InstallDir "$env:USERPROFILE\dotnet"
```

## 5) Teste na sessão atual
Rode:

```sh
$env:PATH="$env:USERPROFILE\dotnet;$env:PATH"
dotnet --info
```

## 6) Deixe permanente no seu usuário
Para não precisar repetir sempre:

```sh
[Environment]::SetEnvironmentVariable("PATH", $env:USERPROFILE + "\dotnet;" + [Environment]::GetEnvironmentVariable("PATH","User"), "User")
[Environment]::SetEnvironmentVariable("DOTNET_ROOT", $env:USERPROFILE + "\dotnet", "User")
```

Depois feche e abra o PowerShell novamente.

## 7) Valide
Rode:

```sh
dotnet --info
dotnet --list-runtimes
dotnet --list-sdks
```
