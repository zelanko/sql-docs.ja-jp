---
title: ステージング中に発生したエラーの表示
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d3bb33d8c3a9237c96fc0bde1becba07df9a7bdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728840"
---
# <a name="view-errors-that-occur-during-staging-master-data-services"></a>ステージング中に発生したエラーの表示 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ステージング処理中に発生したエラーを表示できます。 
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースには、エラーを表示する 2 つのビューがあります。  
  
-   stg.viw_name_MemberErrorDetails (リーフ メンバーまたは統合メンバーの更新用)。  
  
-   stg.viw_name_RelationshipErrorDetails (階層のリレーションシップの更新用)。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースでは、stg.viw_name_MemberErrorDetails ビューまたは stg.viw_name_RelationshipErrorDetails ビューのどちらかに対する SELECT 権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-view-staging-errors"></a>ステージング エラーを表示するには  
  
1.  
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssDE](../includes/ssde-md.md)] データベースの [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] インスタンスに接続します。  
  
2.  新しいクエリを開きます。  
  
3.  名前を viw_Product_MemberErrorDetails などのステージング テーブルの名前に置き換えて、次のテキストを入力します。  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  クエリを実行します。 エラーの詳細が **ErrorDescription** フィールドに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 エラー メッセージの詳細については、「[ステージング処理のエラー (マスター データ サービス)](../master-data-services/staging-process-errors-master-data-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [概要: テーブルからのデータのインポート &#40;マスターデータサービス&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [ステージング処理のトラブルシューティング (マスターデータサービス)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
