---
title: "データ接続のユーザーに委任されませんでした |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 82b5e9a4f63aee2235972f62387367075ff4b8b9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="the-data-connection-user-could-not-be-delegated"></a>データ接続のユーザーに委任されませんでした。
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含む Excel ブックで、Excel Services は、SharePoint の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー インスタンスに接続できない場合にこのエラーを返します。  
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|適用対象|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint|  
|製品バージョン|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|原因|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ プロバイダーを使用しようとしたときに接続が失敗しました。|  
|メッセージ テキスト|データ接続では Windows 認証を使用しており、ユーザーの資格情報を借用できませんでした。 以下の接続を更新できませんでした: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ|  
  
## <a name="explanation"></a>説明  
 このエラー メッセージには複数の原因があります。 それらの原因に共通する要因は、Excel Services が SharePoint のクレーム トークンから有効な Windows ユーザー ID を取得できないことです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含む Excel ブックの場合、次のいずれかの条件に当てはまるときは、このエラーが発生します。  
  
-   Windows トークン サービスに対するクレームが実行されていない。 SharePoint ログ ファイルを表示して、このエラーの原因を確認できます。 SharePoint ログに、"パイプ エンドポイント 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' が、ローカル コンピューター上で見つかりませんでした" というメッセージがある場合、Windows トークン サービスに対するクレームは実行されていません。 このサービスを開始するには、サーバーの全体管理を使用します。その後、[サービス] コンソール アプリケーションでサービスが実行されていることを確認します。  
  
-   ユーザー ID の検証にドメイン コントローラーを使用できない。 Windows トークン サービスに対するクレームでは、キャッシュされた資格情報は使用されません。 接続ごとにユーザー ID が検証されます。 SharePoint ログ ファイルを表示して、このエラーの原因を確認できます。 SharePoint ログに、"IClaimsIdentity から WindowsIdentity を取得できませんでした" というメッセージがある場合、ユーザー ID を認証できなかったことを示します。  
  
-   コンピューターは同じドメインまたは双方向の信頼関係を持つドメインのメンバーである必要がある。  
  
-   Windows ドメイン ユーザー アカウントを使用する必要がある。 これらのアカウントにはユニバーサル プリンシパル名 (UPN) が必要です。  
  
-   オブジェクトを照会するために、Excel Services サービス アカウントに Active Directory のアクセス許可が必要である。  
  
## <a name="user-action"></a>ユーザーの操作  
 次の手順に従って、Windows トークン サービスに対するクレームの状態を確認します。  
  
 その他の場合については、ネットワーク管理者に確認してください。  
  
#### <a name="enable-claims-to-windows-token-service"></a>Windows トークン サービスに対するクレームの有効化  
  
1.  サーバーの全体管理で、[システム設定] の **[サーバーのサービスの管理]**をクリックします。  
  
2.  **[Windows トークン サービスに対するクレーム]**を選択し、 **[開始]**をクリックします。  
  
3.  [サービス] コンソールでサービスが実行されていることも確認します。  
  
    1.  [管理ツール] で、[サービス] をクリックします。  
  
    2.  Windows トークン サービスに対するクレームが実行されていない場合は開始します。  
  
## <a name="see-also"></a>参照  
 [Power Pivot サービス アカウントの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)  
  
  

