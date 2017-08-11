---
title: "Reporting Services ログイン ダイアログ ボックス (SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- sql13.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
caps.latest.revision: 31
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3f9da76454e0b1fe52499471cbb3a04ada2d896e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="reporting-services-login-dialog-box-ssrs"></a>[Reporting Services ログイン] ダイアログ ボックス (SSRS)
  **[Reporting Services ログイン]** ダイアログ ボックスを使用すると、レポートをレポート サーバーにパブリッシュする際に使用する資格情報を指定できます。  
  
-   **注** : プロジェクトの配置プロパティ **TargetServerURL** を設定してから初めてレポートをレポート サーバーにパブリッシュする場合は、サーバー名に **reports** ではなく **server**が含まれることを確認します。 たとえば、 `http://localhost/reportserver`ではなく `http://localhost/reports`のようになります。 ローカル サーバーの `reports` ディレクトリではなく `reportserver` ディレクトリを指定すると、このダイアログ ボックスが間接的に開かれます。 **TargetServerURL** の設定の詳細については、「[配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[サーバー]**  
 レポート サーバーの名前を表示します。 たとえば、 `http://localhost/reportserver`のようにします。 既定のポート 80 と異なるポートを使用するレポート サーバーの場合は、ポート番号を含めます。 たとえば、 `http://localhost:81/reportserver`のようにします。  
  
 **ユーザー名**  
 Web サービスへのログインに使用するユーザー名を入力します。  
  
 **Password**  
 Web サービスへのログインに使用するパスワードを入力します。  
  
## <a name="see-also"></a>参照  
 [データ接続、データ ソース、および接続文字列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [資格情報とレポート データ ソースの接続情報を指定します。](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [レポート デザイナーの F1 ヘルプ](../../reporting-services/tools/report-designer-f1-help.md)  
  
  
