---
title: "catalog.executable_statistics |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bc671da319ee9e8ce71d98df001c3989d497a096
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutablestatistics"></a>catalog.executable_statistics
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  実行される各実行可能ファイル (実行可能ファイルの各繰り返しを含む) に対する行を表示します。  
  
 実行可能ファイルは、パッケージの制御フローに追加するタスクまたはコンテナーです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|Statistics_id|bigint|データの一意の ID。|  
|Execution_id|bigint|実行のインスタンスの一意の ID。<br /><br /> catalog.executions ビューには、実行に関する追加情報が表示されます。 詳細については、次を参照してください。 [catalog.executions & #40 です。SSISDB データベース &#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|bigint|パッケージ コンポーネントの一意の ID。<br /><br /> catalog.executables ビューには、実行可能ファイルに関する追加情報が表示されます。 詳細については、次を参照してください。 [catalog.executables](../../integration-services/system-views/catalog-executables.md)です。|  
|Execution_path|nvarchar(max)|コンポーネントの各繰り返しを含む、パッケージ コンポーネントの実行の完全パス。|  
|Start_time|datetimeoffset(7)|実行可能ファイルが実行前フェーズに入ったときの時刻。|  
|End_time|datetimeoffset(7)|実行可能ファイルが実行後フェーズに入ったときの時刻。|  
|Execution_duration|int|実行可能ファイルの実行に費やされた時間の長さ。 値の単位はミリ秒です。|  
|Execution_result|smallint|使用できる値を次に示します。<br /><br /> 0 (成功)<br /><br /> 1 (失敗)<br /><br /> 2 (完了)<br /><br /> 3 (キャンセル)|  
|Execution_value|sql_variant|実行によって返される値。 これは、ユーザー定義の値です。|  
  
## <a name="permissions"></a>Permissions  
 ビューでは、次の権限のいずれかが必要です。  
  
-   実行のインスタンスに対する READ 権限  
  
-   メンバーシップを**ssis_admin**データベース ロール。  
  
-   メンバーシップを**sysadmin**サーバーの役割です。  
  
  
