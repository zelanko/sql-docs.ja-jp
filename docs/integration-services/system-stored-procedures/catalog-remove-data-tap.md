---
title: catalog.remove_data_tap | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: b77db3e6-478c-441a-a838-82c4de750275
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c4a2140bb7d21598dda17a08ec275fef4365354b
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411024"
---
# <a name="catalogremovedatatap"></a>catalog.remove_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行内のコンポーネント出力からデータ タップを削除します。 データ タップの一意な識別子が実行のインスタンスに関連付けられています。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.remove_data_tap [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>引数  
 [ @data_tap_id = ] *data_tap_id*  
 catalog.add_data_tap ストアド プロシージャを使用して作成されるデータ タップの一意識別子。 *data_tap_id* は **bigint** です。  
  
## <a name="remarks"></a>Remarks  
 パッケージに同じ名前の複数のデータ フロー タスクが含まれる場合、データ タップは指定された名前で最初に見つかったデータ フロー タスクに追加されます。  
  
## <a name="return-codes"></a>リターン コード  
 成功した場合は 0 を返します。  
  
 ストアド プロシージャが失敗した場合は、エラーをスローします。  
  
## <a name="result-set"></a>結果セット  
 なし  
  
## <a name="remarks"></a>Remarks  
 データ タップを削除するには、実行のインスタンスが作成済みの状態 ([catalog.operations &#40;SSISDB データベース&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md) ビューの **status** 列の値が 1) である必要があります。  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   実行のインスタンスの MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 ストアド プロシージャが失敗する原因となる条件を以下に示します。  
  
-   ユーザーに MODIFY 権限がない。  
  
## <a name="see-also"></a>参照  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)   
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
