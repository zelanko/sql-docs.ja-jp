---
title: "検証ストアド プロシージャ (マスター データ サービス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332d3c86-4440-4f12-a6cb-ffbfbccde52c
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4c0606a05973dfbcd8e43f24898c8a9ce01d9fc8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="validation-stored-procedure-master-data-services"></a>検証ストアド プロシージャ (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、ビジネス ルールをモデル バージョンのすべてのメンバーに適用するためにバージョンが検証されます。  
  
 このトピックでは、 **mdm.udpValidateModel** ストアド プロシージャを使用してデータを検証する方法について説明します。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションの管理者であれば、代わりに UI で検証を実行することができます。 詳細については、「[ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  ステージング処理が完了する前に検証を呼び出すと、ステージングが終了していないメンバーは検証されません。  
  
## <a name="example"></a>例  
  
```  
DECLARE @ModelName nVarchar(50) = 'Customer'   
DECLARE @Model_id int   
DECLARE @UserName nvarchar(50)= 'DOMAIN\user_name'   
DECLARE @User_ID int   
DECLARE @Version_ID int   
  
SET @User_ID = (SELECT ID    
                 FROM mdm.tblUser u   
                 WHERE u.UserName = @UserName)   
SET @Model_ID = (SELECT Top 1 Model_ID   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_Name = @ModelName)   
SET @Version_ID = (SELECT MAX(ID)   
                 FROM mdm.viw_SYSTEM_SCHEMA_VERSION   
                 WHERE Model_ID = @Model_ID)  
  
EXECUTE mdm.udpValidateModel @User_ID, @Model_ID, @Version_ID, 1  
  
```  
  
## <a name="parameters"></a>パラメーター  
 このプロシージャのパラメーターを次に示します。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|UserID|ユーザー ID。|  
|Model_ID|モデル ID。|  
|Version_ID|バージョン ID。|  
  
## <a name="see-also"></a>参照  
 [概要: テーブルからデータをインポートする (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [ビジネス ルール &#40; に対してバージョンを検証します。マスター データ サービス &#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
  
