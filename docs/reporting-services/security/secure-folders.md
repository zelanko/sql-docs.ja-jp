---
title: "フォルダーをセキュリティで保護された |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- high-security folders [Reporting Services]
- low-security folders
- folders [Reporting Services], security
- security [Reporting Services], folders
ms.assetid: 0fd91f77-0143-476b-9af0-87293be78e44
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5aad5bbe0b53e2e6669df93496795f4c5b6a3bca
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="secure-folders"></a>フォルダーをセキュリティで保護する
  フォルダーのセキュリティは、レポート サーバーのすべてのコンテンツをセキュリティで保護するための基盤となります。 セキュリティはフォルダー階層全体に継承されるので、フォルダー階層の大きさにかかわらず、特定のアクセス権を許可することができます。  
  
 高レベルのセキュリティを設定したフォルダーは、機密情報を含むレポートを保存したり、ステージング領域として使用できます。たとえば、レポートを最終運用場所に移動する前にテストするためのフォルダーを作成できます。 この領域へのアクセスを制御するため、レポート作成者のみがアイテムを追加および削除できるロールの割り当てと、テスターにレポートの実行を許可しアイテムの追加と削除を禁止するロールの割り当てを定義できます。 テスターとレポート作成者に対し明示的にロールの割り当てが定義されるため、ローカルのシステム管理者以外のユーザーはこのフォルダーにアクセスできません。  
  
 セキュリティ レベルの低いフォルダーは、簡単にアクセスできるようにするレポートの格納場所として使用できます。  
  
 アイテムレベルのセキュリティの基盤となっているフォルダーのセキュリティは、レポート サーバーのフォルダー階層のルート ノードである [ホーム] フォルダーを起点とします。 セキュリティは継承されるので、[ホーム] フォルダーに設定するセキュリティ ポリシーは厳しく制限することを推奨します。 たとえば、[ホーム] フォルダーのロールの割り当てで **Browser** ロールを使用すると、アクセスを表示のみに制限できます。  
  
## <a name="tasks-and-folder-access"></a>タスクとフォルダー アクセス  
 フォルダーに対してロールの割り当てを作成するときは、次の表のタスクを使用することを検討してください。  
  
|使用するタスク|与えられる権限|  
|----------------------|---------------------------|  
|フォルダーの表示|フォルダー階層と、フォルダーがいつ作成および変更されたかを示す読み取り専用のプロパティを表示できます。<br /><br /> ユーザーは、"レポートの表示"、"モデルの表示"、"リソースの表示"、"データ ソースの表示" の各タスクが含まれているロールに割り当てられない限り、フォルダーのアイテムを表示できません。|  
|フォルダーの管理|フォルダーのプロパティの表示、名前や説明の変更、別の場所への移動を行うことができます。 このタスクでは、フォルダーの作成も許可されます。|  
|レポートの管理|ファイル システムからフォルダーにレポートを追加したり、レポート デザイナーからレポート サーバーにレポートをパブリッシュしたりできます。|  
|データ ソースの管理|新しい共有データ ソース アイテムをフォルダーに追加したり、既存の共有データ ソースを変更したりできます。|  
|アイテムへのセキュリティの設定|フォルダーへのアクセスを制御するロールの割り当てを作成および変更できます。 このタスクは、"フォルダーの表示" または "フォルダーの管理" のいずれかと併用する必要があります。 それ以外の場合、ユーザーがアイテムを選択できないので効果がありません。|  
  
## <a name="see-also"></a>「  
 [セキュリティで保護されたレポート、およびリソース](../../reporting-services/security/secure-reports-and-resources.md)   
 [セキュリティで保護された共有データ ソース アイテム](../../reporting-services/security/secure-shared-data-source-items.md)   
 [ネイティブ モード レポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
