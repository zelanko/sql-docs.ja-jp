---
title: "OData 接続マネージャー |Microsoft ドキュメント"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
f1_keywords:
- sql13.dts.designer.odatasource.connectionmanager.f1
- sql13.dts.designer.odataconnectionmanager.f1
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: f54562b59e8c61f723c17e2812ca39cb2e95f273
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="odata-connection-manager"></a>OData 接続マネージャー
 OData 接続マネージャーで OData データ ソースに接続します。 OData ソース コンポーネントでは、OData 接続マネージャーを使用して、OData データ ソースに接続し、サービスからのデータを使用します。 詳細については、「 [OData Source](../../integration-services/data-flow/odata-source.md)」を参照してください。  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>SSIS パッケージへの OData 接続マネージャーの追加  
 次の 3 つの方法で SSIS パッケージに新しい OData 接続マネージャーを追加できます。  
  
-   **[OData ソース エディター]** の **[新規]**  
  
-   **ソリューション エクスプローラー** で **[接続マネージャー]**を右クリックし、 **[新しい接続マネージャー]**をクリックします。 **[接続マネージャーの種類]** の **[ODATA]**をクリックします。  
  
-   右クリックし、**接続マネージャー**デザイナー、および パッケージの下部のペインに**新しい接続**です。 **[接続マネージャーの種類]** の **[ODATA]**をクリックします。  
  
## <a name="connection-manager-authentication"></a>接続マネージャーの認証  
 OData 接続マネージャーは、認証の 5 つのモードをサポートします。  
  
-   [Windows 認証]  
  
-   基本認証 (ユーザー名とパスワードを使用)  

-   Microsoft Dynamics AX Online (ユーザー名とパスワードを使用)
  
-   Microsoft Dynamics CRM Online (ユーザー名とパスワードを使用)
  
-   Microsoft Online Services (ユーザー名とパスワードを使用)  
  
匿名アクセスを使用するには、[Windows 認証] オプションを選択します。  

Microsoft Dynamics AX Online または Microsoft Dynamics CRM にオンライン接続するには使用できません、 **Microsoft Online Services**認証オプション。 Multi-factor authentication の構成されている任意のオプションを使用することはできませんもします。
  
### <a name="specifying-and-securing-credentials"></a>資格情報の指定とセキュリティ保護  
 OData サービスで基本認証が必要とされる場合は、 [OData Connection Manager Editor](../../integration-services/connection-manager/odata-connection-manager-editor.md)でユーザー名とパスワードを指定できます。 エディターに入力した値は、パッケージ内に保存されます。 パスワードの値は、パッケージの保護レベルに応じて暗号化されます。  
  
 ユーザー名とパスワードの値をパラメーター化またはパッケージ外に保存する方法はいくつかあります。 たとえば、パラメーターを使用または SQL Server Management Studio からパッケージを実行するときに直接接続マネージャーのプロパティを設定できます。  
  
## <a name="odata-connection-manager-properties"></a>OData 接続マネージャーのプロパティ  
 次の一覧では、OData 接続マネージャーのプロパティについて説明します。  
  
|||  
|-|-|  
|プロパティ|Description|  
|URL|サービス ドキュメントに対応する URL。|  
|UserName|必要な場合は、認証に使用するユーザー名。|  
|Password|必要な場合は、認証に使用するパスワードです。|  
|SubQueries|接続マネージャーの他のプロパティが含まれます。|  
  
## <a name="odata-connection-manager-editor"></a>[OData 接続マネージャー エディター]
  使用して、 **OData 接続マネージャー エディター**  ダイアログ ボックスの接続を追加または OData データ ソースに対する既存の接続を編集します。  
  
### <a name="options"></a>オプション  
 **接続マネージャー名**  
 接続マネージャーの名前です。  
  
 **サービス ドキュメントの場所**  
 OData サービスに対応する URL。 例: http://services.odata.org/V3/Northwind/Northwind.svc/。  
  
 **[認証]**  
以下のオプションの 1 つを選択します。
-   **Windows 認証**です。 匿名アクセスは、このオプションを選択します。
-   **基本認証** 
-   **Microsoft Dynamics AX オンライン**Dynamics AX オンラインの
-   **Microsoft Dynamics CRM Online** Dynamics CRM Online の
-   **Microsoft Online Services** Microsoft Online Services の

Windows 認証以外のオプションを選択する場合は、入力、**ユーザー名**と**パスワード**です。 

Microsoft Dynamics AX Online または Microsoft Dynamics CRM にオンライン接続するには使用できません、 **Microsoft Online Services**認証オプション。 Multi-factor authentication の構成されている任意のオプションを使用することはできませんもします。

 **接続をテストします。**  
 OData ソースへの接続をテストするには、このボタンをクリックします。  

