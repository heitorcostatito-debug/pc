name: AnyDesk Portátil

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: windows-latest
    timeout-minutes: 10080
    
    steps:
      - name: Baixar AnyDesk
        run: |
          # Baixar AnyDesk
          Invoke-WebRequest -Uri "https://download.anydesk.com/AnyDesk.exe" -OutFile "AnyDesk.exe"
          
          Write-Host "AnyDesk baixado! Iniciando..."
          
          # Iniciar AnyDesk
          .\AnyDesk.exe --start-with-win
          
          Start-Sleep -Seconds 15
          
          # Mostrar ID
          Write-Host "========================================="
          Write-Host "SEU ID DO ANYDESK:"
          .\AnyDesk.exe --get-id
          Write-Host ""
          Write-Host "SENHA: 123456"
          Write-Host "========================================="
          
          # Manter rodando
          while ($true) {
            Start-Sleep -Seconds 600
          }
