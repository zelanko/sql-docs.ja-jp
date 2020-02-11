---
title: ステージング ストアド プロシージャ (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 6a613106-9f87-4caf-a23a-a726fc6561c5
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 8647a1a4529f7c7d4a8258eac5b726da203c7df9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482723"
---
# <a name="staging-stored-procedure-master-data-services"></a>ステージング ストアド プロシージャ (マスター データ サービス)
  
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]からステージング処理を開始する場合、次の 3 つのストアド プロシージャのいずれかを使用します。  
  
-   stg.udp_name_Leaf  
  
-   stg.udp_name_Consolidated  
  
-   stg.udp_name_Relationship  
  
 name は、エンティティの作成時に指定されたステージング テーブルの名前です。  
  
## <a name="staging-process-stored-procedure-parameters"></a>ステージング処理ストアド プロシージャのパラメーター  
 次の表では、これらのストアド プロシージャのパラメーターの一覧を示します。  
  
|パラメーター|[説明]|  
|---------------|-----------------|  
|**VersionName**<br /><br /> 必須|バージョンの名前。 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コレクションの設定に応じて、このパラメーターは大文字と小文字が区別される場合とされない場合があります。|  
|**LogFlag**<br /><br /> 必須|ステージング処理中にトランザクションをログに記録するかどうかを決定します。 設定可能な値は、次のとおりです。<br /><br /> **0**: トランザクションをログに記録しません。<br />**1**: トランザクションをログに記録します。<br /><br /> <br /><br /> 詳細については、「[トランザクション (マスター データ サービス)](transactions-master-data-services.md)」を参照してください。|  
|**BatchTag**<br /><br /> Web サービス以外は必須|ステージング テーブルに指定した **BatchTag** の値。|  
|**Batch_ID**<br /><br /> Web サービスでのみ必須|ステージング テーブルに指定した **Batch_ID** の値。|  
  
### <a name="staging-process-stored-procedure-example"></a>ステージング処理ストアド プロシージャの例  
 次の例は、ステージング ストアド プロシージャを使用してステージング処理を開始する方法を示します。  
  
```  
USE [DATABASE_NAME]  
GO  
  
EXEC[stg].[udp_name_Leaf]  
      @VersionName = N'VERSION_1',  
@LogFlag = 1,  
@BatchTag = N'batch1'  
  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [検証ストアドプロシージャ &#40;マスターデータサービス&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)   
 [ステージング処理を使用したマスターデータサービスのメンバーの読み込みまたは更新](add-update-and-delete-data-master-data-services.md)   
 [ステージング処理中に発生したエラーを表示 &#40;マスターデータサービス&#41;](view-errors-that-occur-during-staging-master-data-services.md)  
  
  
