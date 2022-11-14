#Workflow
</br></br>
część run ma mieć następującą postać, dopisujemy to co pogrubione</br></br>
run: |</br>
          <b>dotnet tool install --global dotnet-coverage</b></br>
          .\.sonar\scanner\dotnet-sonarscanner begin /k:"xxx" /o:"xxx" /d:sonar.login="${{ secrets.SONAR_TOKEN }}" /d:sonar.host.url="https://sonarcloud.io" <b>/d:sonar.cs.vscoveragexml.reportsPaths=coverage.xml</br>
          dotnet build --configuration Release</br>
          dotnet-coverage collect 'dotnet test' -f xml -o 'coverage.xml'</b></br>
          .\.sonar\scanner\dotnet-sonarscanner end /d:sonar.login="${{ secrets.SONAR_TOKEN }}"</br>
