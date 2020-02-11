---
title: OData 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0b0596e9ba13e617b6f4eef961966bcc07107314
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833110"
---
# <a name="odata-connection-manager"></a>OData 接続マネージャー
  OData 接続マネージャーを使用すると、パッケージは OData ソースに接続できます。 OData ソース コンポーネントは OData 接続マネージャーを使用して OData ソースに接続し、サービスから取得したデータを使用します。 これらのコンポーネントのインストール手順などの詳細については、「 [OData ソース](../data-flow/odata-source.md)」セクションを参照してください。  
  
## <a name="adding-connection-manager-to-an-ssis-package"></a>SSIS パッケージへの接続マネージャーの追加  
 次の 3 とおりの方法で、SSIS パッケージに新しい OData 接続マネージャーを追加できます。  
  
-   **[OData ソース エディター]** の **[新規]** ボタンをクリックします。  
  
-   **ソリューションエクスプローラー**で [**接続マネージャー** ] フォルダーを右クリックし、[**新しい接続マネージャー**] をクリックします。 **[接続マネージャーの種類]** の **[ODATA]** をクリックします。  
  
-   パッケージデザイナーの下部にある [**接続マネージャー** ] ペインを右クリックし、[**新しい接続**] を選択します。[**接続マネージャーの種類**] で [ **ODATA** ] を選択します。  
  
## <a name="connection-manager-authentication"></a>接続マネージャーの認証  
 OData 接続マネージャーでは、2 つの認証モードがサポートされています。  
  
-   [Windows 認証]  
  
-   基本認証 (ユーザー名とパスワード)  
  
 匿名アクセスを使用するには、[Windows 認証] オプションを選択します。  
  
### <a name="specifying-and-securing-credentials"></a>資格情報の指定とセキュリティ保護  
 OData サービスで基本認証が必要な場合は、 [Odata 接続マネージャーエディター](../odata-connection-manager-editor.md)でユーザー名とパスワードを指定できます。 エディターに入力した値は、パッケージ内に保存されます。 パスワードの値は、パッケージの保護レベルに応じて暗号化されます。  
  
 ユーザー名とパスワードの値を外部化またはパラメーター化する複数の方法があります。 
  [!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)] でこの作業を実行する 2 つの主要な方法は、パラメーターを使用するか、SQL Server Management Studio を使用してパッケージを実行するときに接続マネージャーのプロパティを直接設定することです。  
  
## <a name="odata-connection-manager-properties"></a>OData 接続マネージャーのプロパティ  
 次の一覧で、変更する可能性のある OData 接続マネージャーのプロパティの一部を説明します。  
  
|||  
|-|-|  
|プロパティ|[説明]|  
|url|サービス ドキュメントに対応する URL。|  
|UserName|基本認証で使用するユーザー名。|  
|Password|基本認証で使用するパスワード。|  
|ConnectionString|接続マネージャーの他のプロパティを反映します。|  
  
## <a name="see-also"></a>参照  
 [[OData 接続マネージャー エディター]](../odata-connection-manager-editor.md)  
  
  
