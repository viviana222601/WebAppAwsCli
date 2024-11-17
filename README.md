1. Instalar AWS CLI para Windows
- https://awscli.amazonaws.com/AWSCLIV2.msi
2. Una vez instalado abrir consola o powershell y ejecutar
- AWS –-versión
3. Posterior a esto configuramos el aws_access_key_id y aws_secret_access_key que encontramos en AWS Details
![image](https://github.com/user-attachments/assets/f44e27bb-0fd5-4dde-8505-e335aed54874)


Adicional configuramos la zona horaria y el formato json
4. Ahora creamos una carpeta donde estará nuestro proyecto y desde powershell nos ubicamos en la carpeta
5. Ejecutamos para java:
cdk init app --language java
6. Con esto nos bajara toda la estructura del proyecto y estas dos clases:
![image](https://github.com/user-attachments/assets/8755c36d-d61b-4e73-b057-48eb29d1475c)

7. En HelloCdkApp configuramos el AWS account ID que obtenemos del comando:
- aws sts get-caller-identity --query "Account" --output text
y la zona del comando:
- aws configure get region
![image](https://github.com/user-attachments/assets/44eb6b90-cc41-4075-ab50-662ff3c0ec41)

8. Ahora traemos la Plantilla de Bootstrap con CloudFormation:

powershell "cdk bootstrap --show-template | Out-File -encoding utf8 bootstrap-template.yaml"
9. En el Proyecto abrimos el archivo y en el nodo Resources comentamos desde el FilePublishingRole al CloudFormationExecutionRole esto debido a que esta cuenta por ser estudiante no tiene todo el módulo de IAM.
10. En el nodo FileAssetsBucketEncryptionKey debemos cambiar el parámetro 
![image](https://github.com/user-attachments/assets/97c08cee-2488-42c1-aa15-f2ee568fa014)

11. Ejecutamos nuevamente:
bootstrap-template.yaml"
12. Ejecutamos
cdk Bootstrap
13. Compilamos:
mvn compile
14. Creamos la función lambda que se encuentra en la clase HelloCdkStack de la línea 31 a 42 
15. Definimos la URL de la lambda
![image](https://github.com/user-attachments/assets/91f78c73-722c-4212-94ae-b3e803d435ec)
![image](https://github.com/user-attachments/assets/8466fec0-be0a-4add-a288-a5832156a3e3)


16. Compilamos y sintetizamos 
cdk synth
17. Desplegamos
cdk deploy
18. Nos arrojara una URL a la cual accedemos
![image](https://github.com/user-attachments/assets/23f602b0-e17a-4c7e-b21a-b11465ec278b)
![image](https://github.com/user-attachments/assets/950a3053-142c-45da-a774-e67bedc546ef)
![image](https://github.com/user-attachments/assets/e319561d-3ea6-4f7e-8dcc-547c8f328c2d)



