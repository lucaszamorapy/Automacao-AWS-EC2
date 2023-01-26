import os = importando os
import boto3 = sdk para a aws (biblioteca para usar o ec2)

AMI = os.environ['AMI']
INSTANCE_TYPE = os.environ['INSTANCE_TYPE']		----> criando variaveis para o contexto do ec2
KEY_NAME = os.environ['KEY_NAME']
SUBNET_ID = os.environ['SUBNET_ID']

ec2 = boto3.resource('ec2') ---> criando uma variavel para o boto3(ec2) com a função resource

def lambda_handler(event, context): ----> na lambda vai conter o evento e o contexto


*evento*  instance = ec2.create_instances(			----> criar instancias ec2(seria o boto3)		
*contexto* ImageId=AMI,								----> precisa de AMI
			 InstanceType=INSTANCE_TYPE,			----> um tipo de instancia									 
	        KeyName=KEY_NAME,						----> uma key name
			 SubnetId=SUBNET_ID,						----> uma subnet id
			 MaxCount=1,     							----> quantas máquinas voce quer criar
			 MinCount=1
)

print("New instance created:", instance[0].id) ---> imprimir o id da instancia