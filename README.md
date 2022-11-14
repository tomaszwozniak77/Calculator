#Workflow
część run ma mieć następującą postać, dopisujemy to co pogrubione
run: |
          *dotnet tool install --global dotnet-coverage*
          .\.sonar\scanner\dotnet-sonarscanner begin /k:"xxx" /o:"xxx" /d:sonar.login="${{ secrets.SONAR_TOKEN }}" /d:sonar.host.url="https://sonarcloud.io" */d:sonar.cs.vscoveragexml.reportsPaths=coverage.xml
          dotnet build --configuration Release
          dotnet-coverage collect 'dotnet test' -f xml -o 'coverage.xml'*
          .\.sonar\scanner\dotnet-sonarscanner end /d:sonar.login="${{ secrets.SONAR_TOKEN }}"
