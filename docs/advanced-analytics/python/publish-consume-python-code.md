---
title: "発行および Python コードを使用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 281f3beb3678d74fb03b3dc68a4a9b58d44f261e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="publish-and-consume-python-web-services"></a>発行および Python web サービスの利用

Web サービスに、作業用 Python ソリューションを展開するには、Microsoft Machine Learning のサーバーの操作運用の機能を使用します。 このトピックでは、正常に発行し、ソリューションを実行する手順について説明します。

この記事の対象読者は、データ サイエンティストは、Microsoft Machine Learning のサーバーでホストされる web サービスとしての Python コードまたはモデルを発行する方法を学習します。 アプリケーションで使用する方法も説明、コードまたはモデル。 この記事では、Python に習熟していることを前提としています。

> [!IMPORTANT]
>
> このサンプルは、Machine Learning Server (スタンドアロン) に含まれて、Machine Learning のサーバーのバージョンで機能を使用して Python のバージョンの開発された**9.1.0**です。
 > 
 > 次のリンクを クリックすると、再発行 Machine Learning のサーバーで、新しいライブラリを使用して、同じサンプルを参照してください。 参照してください[展開および Python で web サービスを管理](https://docs.microsoft.com/machine-learning-server/operationalize/python/how-to-deploy-manage-web-services)です。

**適用されます Microsoft R Server (スタンドアロン)。**

## <a name="overview-of-workflow"></a>ワークフローの概要

よう Python web サービスを使用する公開からワークフローにまとめることができます。

1. 満たすため、[前提条件](#prereq)のコア API Swagger ドキュメントから Python クライアント ライブラリを生成します。
2. Python スクリプトには、認証とヘッダーのロジックを追加します。
3. Python セッションを作成する、環境を準備し、環境を保持するスナップショットを作成します。
4. Web サービスを発行し、このスナップショットを埋め込みます。
5. Web サービスで試してみてから、によって、セッションで使用します。
6. これらのサービスを管理します。

![Swagger ワークフロー](./media/data-scientist-python-workflow.png)

この記事では、ワークフローの各手順について説明し、虹彩データセットを使用したサンプル Python コードが含まれています。

## <a name="sample-code"></a>サンプル コード

このサンプル コードが想定が満たされて、[の前提条件](#prereq)その Swagger から Python クライアント ライブラリを生成するファイルとを使った Autorest です。

コード ブロックの後に、すべてのプロセスに関する詳細な説明と詳細なチュートリアルがあります。

> [!IMPORTANT]
> この例は、ローカルを使用して`admin`アカウントを認証します。 ただし、資格情報を置き換える必要がありますと[認証メソッド](#python-auth)管理者によって構成します。

```python
##################################################
##       IMPORT GENERATED CLIENT LIBRARY        ##
##################################################

# Import the generated client library. 

import deployrclient

# This example is intended for use with Microsoft R Server 9.0.1. 
# If you are using a newer version of Machine Learning Server, 
# use the mrs_server library instead.

##################################################
##              AUTHENTICATION                  ##
##################################################

#Using client library generated from Autorest
#Create client instance and point it at an R Server. 
#In this case, R Server is local.
client = deployrclient.DeployRClient("http://localhost:12800")
# To use ML Server, replace with mrs_server.MRSServer()

#Define the login request and provide credentials 
#Update values with the connection parameters from your admin
login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")

#Make a call to the /login API. 
#Store the returned an access token in a variable.
token_response = client.login(login_request)

#Add the returned access token to the headers variable.
headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}

#Verify that the server is running.
#Remember to include `headers` in all requests!
status_response = client.status(headers) 
print(status_response.status_code)


##################################################
##        CREATE SESSION, MODEL, SNAPSHOT       ##
##################################################

#Since already logged in, create a Python session.
#Define session using name (`Session 1`) and `runtime_type="Python"`.
#Remember to specify the Python runtime type.
create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")

#Make the call to start the session. 
#Remember to include headers in all method calls to the server.
#Returns a session ID.
response = client.create_session(create_session_request, headers) 
   
#Store the session ID in a variable called `session_id` 
#to be able to identify it later at execution time.
session_id = response.session_id

#Create model - Import SVM and datasets from the SciKit-Learn library
execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define the untrained Support Vector Classifier (SVC) object
#and the dataset to be preloaded.
execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
#Now, go create the object and preload Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)
#Report if it was a success
execute_response.success
   
#Define two rows from the Iris Dataset as a sample for scoring
workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

#Define how to train the classifier model; what to predict; what to return
execute_request = deployrclient.models.ExecuteRequest(
    "clf.fit(iris.data, iris.target)\n"+
    "result=clf.predict(species_1)\n"+
    "other_result=clf.predict(species_2)",
    [workspace_object,workspace_object_2], #Input
    ["result", "other_result"]) #Output

#Now, go train that model on the Iris Dataset in R Server
execute_response = client.execute_code(session_id,execute_request, headers)

#If successful, print name and result of each output parameter. Else, print error.
if(execute_response.success):
    for result in execute_response.output_parameters:
        print("{0}: {1}".format(result.name,result.value))
else:
    print (execute_response.error_message)

#Create a snapshot of the current session
response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
#Return the snapshot ID for reference when you publish later.
response.snapshot_id
#If you forget the ID, list snapshots to get the ID again.
for snapshot in client.list_snapshots(headers):
    print(snapshot)

##################################################
##        PUBLISH AS A SERVICE IN PYTHON        ##
##################################################

#Define a web service that determines the iris species by scoring 
#a vector of sepal length and width, petal length and width

#Set `flower_data` for the sepal and petal length and width
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
#Set `iris_species` for the species of iris
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")

#Define the publish request for the web service and its arguments.
#Specify the code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

#Publish the service using the specified name (iris), version (V1.0)
client.publish_web_service_version("Iris", "V1.0", publish_request, headers)

##################################################
##           CONSUME SERVICE IN PYTHON          ##
##################################################

# Inspect holdings and metadata for service Iris V1.0.
for service in client.get_web_service_version("Iris","V1.0", headers):
    #print service metadata (description, who published,...)
    print(service)
    #Print input and output parameters as defined in service definition object
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Import the requests library to make requests on the server
import requests
#Import the JSON library to use for pretty printing of json responses
import json

#Create a requests `Session` object.
s = requests.Session()

#Record the R Server endpoint URL hosting the web services you created before
url = "http://localhost:12800"

#Give the request.Session object the authentication headers 
#so you don't have to repeat it with each request.
s.headers = headers

#Retrieve the service-specific swagger file using the requests library.
swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

#Either, download service-specific swagger file using the json library.
with open('iris_swagger.json','w') as f:
   (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

#Or, print just what you need from the Swagger file, 
#such as the routing paths for the endpoints to be consumed.
print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

#Or, print input and output parameters as defined in the Swagger.io format
print("Input")
print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
print("Output")
print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))

#Make the request to consume the service using these flower_data inputs
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
#Print the output
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Use input from another Iris species.
resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

##################################################
##          MANAGE SERVICES IN PYTHON           ##
##################################################

#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)

#Or, publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))

#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))

#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

## <a name="walkthrough"></a>チュートリアル

このセクションより詳細で、コードがどのように動作するかについて説明します。


### <a name="prereq"></a>手順 1 です。 前提条件となるクライアント ライブラリを作成します。

発行、Python コードとモデルいう Microsoft Machine Learning のサーバーを開始する前に、このリリースで提供される Swagger ドキュメントを使用してクライアント ライブラリを生成する必要があります。

1. Swagger コード ジェネレーターをローカル コンピューターにインストールし、慣れることです。 Python で API のクライアント ライブラリの生成に使用されます。 一般的なツールのインクルード[Azure AutoRest](https://github.com/Azure/autorest) (Node.js が必要) および[Swagger Codegen](https://github.com/swagger-api/swagger-codegen)です。 

2. Machine Learning のサーバーのバージョンのコア Api を含む Swagger ファイルをダウンロードします。 このファイルには、REST リソースとそれらのリソースに対して呼び出すことができる操作の一覧を定義する Swagger テンプレートが含まれています。 このファイルを見つけることができます`https://microsoft.github.io/deployr-api-docs/swagger/<version>/rserver-swagger-<version>.json`ここで、 `<version>` 3 桁の数字 R Server のバージョン番号です。 

   たとえば、R サーバー 9.1 からダウンロードする: https://microsoft.github.io/deployr-api-docs/9.1.0/swagger/rserver-swagger-9.1.0.json

3. 渡すことによって、静的に生成されたクライアント ライブラリを生成、 `rserver-swagger-<version>.json` Swagger コード ジェネレーターへのファイルし、言語を示すを指定します。 この場合、Python を指定する必要があります。  

    たとえば、Python クライアント ライブラリを生成する AutoRest を使用する場合、ようになりますこれには、3 桁の数字が R サーバーのバージョン番号を表します。
    
    `AutoRest.exe -Input rserver-swagger-9.1.0.json -CodeGenerator Python  -OutputDirectory C:\Users\rserver-user\Documents\Python`

4. 一部のカスタム ヘッダーを示し、ライブラリのスタブを生成されたクライアントを使用する前に他の変更を加えることができますもします。 参照してください、[コマンド ライン インターフェイス](https://github.com/Azure/autorest/blob/master/docs/user/cli.md)GitHub で別の構成オプションと、名前空間の名前変更などの設定の詳細についてのドキュメントです。
   
5. さまざまな API の呼び出しを表示することができます、コア クライアント ライブラリについて説明します。 

    この例では、いくつかのディレクトリと、ローカル システム上の Python クライアント ライブラリのファイル Autorest が生成されます。 名前空間 (とディレクトリ) は、既定では、`deployrclient`し、次のようになります。
   
   ![Autorest 出力パス](./media/data-scientist-python-autorest.png)

    この既定の名前空間のクライアント ライブラリ自体と呼ばれる`deploy_rclient.py`です。 このファイルを開くには、Visual Studio などの IDE で、次のように表示されます。
   
   ![Python クライアント ライブラリ](./media/data-scientist-python-client-library.png)


### <a name="step-2-add-authentication-and-header-logic"></a>手順 2. 認証とヘッダーのロジックを追加します。

すべての Api に認証が必要なことに注意してください。API を使用して呼び出しを行うときにそのため、すべてのユーザーを認証する必要があります、 `POST /login` API または Azure Active Directory (AAD) を通じてします。 

このプロセスを簡略化は、ユーザーが、呼び出しごとに自分の資格情報提供する必要がないように、ベアラー アクセス トークンが発行されます。  このベアラー トークンは、保護されたリソースに対する"bearer"アクセスを許可する簡易的なセキュリティ トークン。 この場合は、Machine Learning サーバーの Api です。 ユーザーが認証されると、アプリケーションは認証では、意図した相手の成功したことを確認するユーザーのベアラー トークンを検証する必要があります。 これらのトークンの管理に関する詳細についてを参照してください。[セキュリティのアクセス トークン](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens)です。

コア Api とやり取りする前に最初に認証、ベアラー アクセス トークンを使用して、[認証方法](https://msdn.microsoft.com/microsoft-r/operationalize/security-authentication)管理者によって構成され、後続の要求では、各ヘッダーに含めること。

1. これからアクセスできるように、優先 Python Jupyter、Visual Studio、VS コードでは、iPython など、コード エディターに、クライアント ライブラリをインポートすることによって開始します。

   クライアント ライブラリの親ディレクトリを指定します。 この例では、Autorest 生成されたクライアント ライブラリが下にある`C:\Users\rserver-user\Documents\Python\deployrclient`:

   ```python
   # Import the generated client library
   import deployrclient
   ```

2. アプリケーションをローカル コンピューターから Machine Learning のサーバーへの接続を定義する、資格情報を提供、アクセス トークンをキャプチャ、ヘッダーにそのトークンを追加するには、認証ロジックを追加します。 すべての後続の要求のヘッダーを使用しています。  管理者によって定義されている認証方法を使用します。 基本的な管理アカウント、Active Directory または LDAP (AD または LDAP)、または Azure Active Directory (AAD)。

   **AD または LDAP または`admin`アカウントの認証**

   呼び出す、 `POST /login` API を認証するためにします。 渡す、`username`と`password`ローカルの管理者では、Active Directory が有効になっている場合は、LDAP アカウント情報を渡すこともできます。 さらに、マシン学習サーバーは、ベアラー/アクセス トークンを発行します。 認証されると、ユーザーが、トークンがまだ有効では、ヘッダーが各要求と一緒に送信される限り、資格情報を指定する必要がありません。 接続の設定がわからない場合は、管理者に問い合わせてください。

   ```python
   #Using client library generated from Autorest
   #Create client instance and point it at an R Server. 
   #In this case, R Server is local.
   client = deployrclient.DeployRClient("http://localhost:12800")
   
   #Define the login request and provide credentials. 
   #Update values with the connection parameters from your admin.
   login_request = deployrclient.models.LoginRequest("<<your-username>>","<<your-password>>")
   #Make a call to the /login API. 
   #Store the returned an access token in a variable.
   token_response = client.login(login_request)
   ```

   **Azure Active Directory (AAD) の認証**

   AAD 資格情報、権限、およびクライアント ID を渡す AAD をさらに、発行、[ベアラー アクセス トークン](https://msdn.microsoft.com/microsoft-r/operationalize/security-access-tokens)です。 認証されると、ユーザーが、トークンがまだ有効では、ヘッダーが各要求と一緒に送信される限り、資格情報を指定する必要がありません。 接続の設定がわからない場合は、管理者に問い合わせてください。

   ```python
   #Import the AAD authentication library
   import adal
   
   #Define the login request and provide credentials. 
   #Use the AAD connection parameters provided by your admin.
   url = "http://localhost:12800"
   authuri = https://login.windows.net,
   tenantid = "<<AAD_DOMAIN>>", 
   clientid = "<<NATIVE_APP_CLIENT_ID>>", 
   resource = "<<WEB_APP_CLIENT_ID>>", 
   
   #Acquire authentication token using AAD Device Code Login
   context = adal.AuthenticationContext(authuri+'/'+tenantid, api_version=None)
   code = context.acquire_user_code(resource, clientid)
   print(code['message'])
   token = context.acquire_token_with_device_code(resource, code, clientid)
   #The authentication code returned must be entered at https://aka.ms/devicelogin 
   ```     

3. 追加、`Bearer`アクセス トークンと Machine Learning のサーバーが現在実行されていることを確認します。  このトークンが認証中に返されたと**すべての後続の要求ヘッダーに含まれる必要があります**です。 この例では、Autorest によって生成されたクライアント ライブラリを使用します。

   > [!IMPORTANT]
   > すべての API 呼び出しを認証する必要があります。 そのため、すべて 1 つの要求するトークンを含むヘッダーをインクルードする注意してください。

   ```python
   #Add the returned access token to the headers variable.
   headers = {"Authorization": "Bearer {0}".format(token_response.access_token)}
   
   #Verify that the server is running.
   #Remember to include `headers` in every request!
   status_response = client.status(headers) 
   print(status_response.status_code)
   ```

### <a name="step-3-prepare-session-and-code"></a>手順 3. セッションとコードを準備します。

認証の後に、Python セッションを開始し、後で発行するためのモデルを作成できます。 Web サービスでは、任意の Python コードまたはモデルを含めることができます。 セッション環境をセットアップした後できるでもとして保存するスナップショットようにする必要があったため、前に、セッションを再読み込みすることができます。 

> [!IMPORTANT]
> 必ず含めて`headers`すべての要求にします。

1. R Server での Python セッションを作成します。 名前および Python 言語を指定してください (`runtime_type="Python"`)。  Python ランタイムの型を設定しなかった場合は、既定値は r です。

   これは、Autorest によって生成されたクライアント ライブラリを使用する例の続きです。

   ```python
   #Since already logged in, create a Python session.
   #Define session using name (`Session 1`) and `runtime_type="Python"`.
   #Remember to specify the Python runtime type.
   create_session_request = deployrclient.models.CreateSessionRequest("Session 1", runtime_type="Python")
   
   #Make the call to start the session. 
   #Remember to include headers in every method call to the server.
   #Returns a session ID.
   response = client.create_session(create_session_request, headers) 
   
   #Store the session ID in a variable called `session_id` 
   #to be able to identify it later at execution time.
   session_id = response.session_id
   ```

2. 作成または web サービスとして公開されます Python でモデルを呼び出す

   この例では、SciKit についてサポート ベクター マシン (SVM) モデル、Iris データセット Machine Learning のサーバーのリモート インスタンス上をトレーニングします。  このデータセットがから利用可能な[scikit-サイトを学習](http://scikit-learn.org/stable/auto_examples/datasets/plot_iris_dataset.html)です。

   ```python
   #Import SVM and datasets from the SciKit-Learn library
   execute_request = deployrclient.models.ExecuteRequest("from sklearn import svm\nfrom sklearn import datasets")
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define the untrained Support Vector Classifier (SVC) object
   #and the dataset to be preloaded.
   execute_request = deployrclient.models.ExecuteRequest("clf=svm.SVC()\niris=datasets.load_iris()\nnames={0:'I. setosa',1:'I. versicolor',2:'I. virginica'}")
   #Now, go create the object and preload Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)
   #Report if it was a success
   execute_response.success
   
   #Define two rows from the Iris Dataset as a sample for scoring
   workspace_object = deployrclient.models.WorkspaceObject("species_1",[7,3.2,4.7,1.4])
   workspace_object_2 = deployrclient.models.WorkspaceObject("species_2",[3,2.6,3,2.5])

   #Define how to train the classifier model; what to predict; what to return
   execute_request = deployrclient.models.ExecuteRequest(
       "clf.fit(iris.data, iris.target)\n"+
       "result=clf.predict(species_1)\n"+
       "other_result=clf.predict(species_2)",
       [workspace_object,workspace_object_2], #Input
       ["result", "other_result"]) #Output

   #Now, go train that model on the Iris Dataset in R Server
   execute_response = client.execute_code(session_id,execute_request, headers)

   #If successful, print name and result of each output parameter. Else, print error.
   if(execute_response.success):
       for result in execute_response.output_parameters:
           print("{0}: {1}".format(result.name,result.value))
   else:
       print (execute_response.error_message)
   ```

3. スナップショットを作成するこの Python のため、この環境は、web サービスに保存してでは、再現セッションが時間を消費します。 スナップショットは、準備された環境を特定のライブラリ、オブジェクト、モデル、ファイル、および成果物を含む必要がある場合に便利です。 スナップショットは、作業ディレクトリとワークスペース全体を保存します。 ただし、発行するときに作成したスナップショットのみを使用できます。

   ```python
   #Create a snapshot of the current session.
   response = client.create_snapshot(session_id, deployrclient.models.CreateSnapshotRequest("Iris Snapshot"), headers)
   
   #Return the snapshot ID for reference when you publish later.
   response.snapshot_id
   
   #If you forget the ID, list snapshots to get the ID again.
   for snapshot in client.list_snapshots(headers):
       print(snapshot)
   ```

  > [!NOTE] 
   > スナップショットは、環境の依存関係の web サービスを発行するときにも使用できますが、消費時間のパフォーマンスに影響があります。  最適なパフォーマンスをワークスペース オブジェクトのみと必要とする残りの部分を削除しておくことを確認して、スナップショットのサイズを慎重に検討してください。 セッションでは、Python を使用することができます`del`関数または[、 `deleteWorkspaceObject` API 要求](https://microsoft.github.io/deployr-api-docs/#delete-workspace-object)不要なオブジェクトを削除します。 

### <a name="step-4-publish-the-model"></a>手順 4. モデルをパブリッシュします。 

クライアント ライブラリが生成され、アプリケーションに認証ロジックを作成したら、Python セッションを作成、モデルを作成し、そのモデルを使用して web サービスを公開する Api のコアと対話できます。

いくつかの点に注意してください。

+ API の呼び出しを実行する前に認証する必要があります。 このため、含める`headers`すべての要求数。
+ Web サービスが、Python サービスとして登録されていることを確認するには必ず指定して`runtime_type="Python"`です。 Python ランタイムの型を設定しなかった場合は、既定値は r です。
+ Sepal sepal 幅、花びら長さ、および花びら幅を持つベクトル スコア付けが必要です。

次のコードは、Python web サービスとして、SVM モデルを公開します。 この web サービスには、渡された値に基づいて予測カテゴリが生成されます。

```python
   #Set `flower_data` for the sepal and petal length and width
   flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
   #Set `iris_species` for the species of iris
   iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "vector")
   
   #Define the publish request for the web service and its arguments.
   #Specify the code, inputs, outputs, and snapshot.
   #Don't forget to set runtime_type="Python"`.
   publish_request = deployrclient.models.PublishWebServiceRequest(
       code = "iris_species = [names[x] for x in clf.predict(flower_data)]", 
       input_parameter_definitions = [flower_data], 
       output_parameter_definitions = [iris_species],
       runtime_type = "Python",
       snapshot_id = response.snapshot_id)

   #Publish the service using the specified name (iris), version (V1.0)
   client.publish_web_service_version("Iris", "V1.0", publish_request, headers)
```

### <a name="step-5-consume-the-web-service"></a>手順 5. Web サービスを使用します。

このセクションでは、その作成元の同じセッションでサービスを利用する方法を示します。

1. 同じセッションで、サービスのサービス保有とメタデータを取得します。

   ```python
   # Inspect holdings and metadata for service Iris V1.0.
   for service in client.get_web_service_version("Iris","V1.0", headers):
       #print service metadata (description, who published,...)
       print(service)
       #Print input and output parameters as defined in service definition object
       print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
       print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
   ```

2. サービスの保有を確認し、使用するための準備します。 
   ```python
   #Import the requests library to make requests on the server
   import requests
   #Import the JSON library to use for pretty printing of json responses
   import json

   #Create a requests `Session` object.
   s = requests.Session()

   #Record the R Server endpoint URL hosting the web services you created
   url = "http://localhost:12800"

   #Include the request.Session object in the authentication headers.
   #By doing so, you don't need to repeat it with each request.
   s.headers = headers

   # Retrieve the service-specific Swagger file using the requests library.
   swagger_resp = s.get(url+"/api/Iris/V1.0/swagger.json")

   #You can download a service-specific Swagger file using the json library.
   with open('iris_swagger.json','w') as f:
      (json.dump(client.get_web_service_swagger("Iris","V1.0",headers),f, indent = 1))

   #Or, you can print just what you need from the Swagger file. 
   #This example gets the routing paths for the endpoints to be consumed.
   print(json.dumps(swagger_resp.json()["paths"], indent = 1, sort_keys = True))

   #You can also print input and output parameters as defined in the Swagger.io format
   print("Input")
   print(json.dumps(swagger_resp.json()["definitions"]["InputParameters"], indent = 1, sort_keys = True))
   print("Output")
   print(json.dumps(swagger_resp.json()["definitions"]["WebServiceResult"], indent = 1, sort_keys = True))
   ```

3. いくつかを指定することによって、サービスを使用する入力と Iris 種を取得します。 
   ```python
   #Make the request to consume the service using these flower_data inputs
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[7,3.2,4.7,1.4]})
   #Print the output
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[3,2.6,3,2.5]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))

   ##Use input from another Iris species.
   resp = s.post(url+"/api/Iris/V1.0",json={"flower_data":[5.1,3.5,1.4,.2]})
   print(json.dumps(resp.json(), indent = 1, sort_keys = True))
   ```

## <a name="managing-the-services"></a>サービスを管理します。

Web サービスを作成したら、これでは、更新に削除、またはそのサービスを再発行します。 R Server (または Machine Learning サーバー) を使用してホストされているすべての web サービスの一覧を表示することもできます。

### <a name="update-a-web-service"></a>Web サービスを更新します。

 この例では、このサービスを使用することがあります人に便利な説明を追加するサービスを更新します。

```python
#Define what needs to be updated. Here we add a description.
#Be sure to specify the runtime_type again.
update_request = deployrclient.models.PublishWebServiceRequest(
    description = "Determines iris species using length and width of sepal and petal", runtime_type = "Python")
#Now update it by specifying the service name and version number
client.patch_web_service_version("Iris", "V1.0", update_request, headers)
```

コード、モデル、説明、入力、出力、および詳細を変更する web サービスを更新することができます。

### <a name="publish-another-version"></a>別のバージョンを発行します。

この例では、サービスを返します Iris 種の代わりに、文字列のリストとしての文字列として。

```python
#Publish another version of the web service, but this time 
#the service returns the species as a string instead of list of strings.
flower_data = deployrclient.models.ParameterDefinition(name = "flower_data", type = "vector")
iris_species = deployrclient.models.ParameterDefinition(name = "iris_species", type = "string")
 
#Define the publish request for the service and its arguments.
#Specify the changed code, inputs, outputs, and snapshot.
#Don't forget to set runtime_type="Python"`.
publish_request = deployrclient.models.PublishWebServiceRequest(
    code = "iris_species = [names[x] for x in clf.predict(flower_data)][0]",
    description = "Determines the species of iris, based on Sepal Length, Sepal Width, Petal Length and Petal Width",
    input_parameter_definitions = [flower_data],
    output_parameter_definitions = [iris_species],
    runtime_type = "Python",
    snapshot_id = response.snapshot_id)
 
#Now, publish the service with version (V2.0)
client.publish_web_service_version("Iris", "V2.0", publish_request, headers)
 
#Make request to consume service using these flower_data inputs; print output
resp = s.post(url+"/api/Iris/V2.0",json={"flower_data":[5.1,3.5,1.4,.2]})
print(json.dumps(resp.json(), indent = 1, sort_keys = True))
```

このパターンを使用して、同じ web サービスの複数のバージョンを発行できます。 

### <a name="list-services"></a>サービスの一覧表示

このサンプルでは、他のユーザーによってまたは別の言語で作成されたものを含む、すべての web サービスの一覧を取得します。

```python
#Return the list of all existing web services.
for service in client.get_all_web_services(headers):
    #print the service information
    print(service)
    #Print each input and output parameter
    print("Input Parameters: {0}".format([str(parameter) for parameter in service.input_parameter_definitions]))
    print("Output Parameters: {0}".format([str(parameter) for parameter in service.output_parameter_definitions]))
``` 

### <a name="delete-services"></a>サービスを削除します。

この例では、発行した 2 つ目の web サービスのバージョンを削除します。

```python
#Delete the second version we just published.
client.delete_web_service_version("Iris","V2.0",headers)
```

作成した任意のサービスを削除することができます。 適切なアクセス許可を持つロールに割り当てられた場合にのみ、他のサービスを削除することができます。