---
title: sysssislog (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtslog90_TSQL
- sysdtslog90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssislog system table
ms.assetid: 7fa288a1-81e3-42a0-82f6-8a59019693d0
caps.latest.revision: 40
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0f60ec3735bc89c7e729ac6ec01e6f62f126c51f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysssislog-transact-sql"></a>sysssislog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パッケージやパッケージのタスク、およびコンテナーによって実行時に生成される各ログ エントリに対して、1 行のデータを格納します。 このテーブルは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールするときに msdb データベースに作成されます。 ログ記録が別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに記録されるように構成する場合、ここで説明する形式の sysssislog テーブルが、指定されたデータベースに作成されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] このテーブルにログ エントリを書き込みます**のみ**パッケージを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ プロバイダーです。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|ログ エントリの一意識別子。|  
|イベント|**sysname**|ログ エントリを生成したイベントの名前。|  
|computer|**nvarchar**|ログ エントリの生成時にパッケージが実行されていたコンピューター。|  
|演算子 (operator)|**nvarchar**|ログ エントリを生成したパッケージを実行したユーザーの名前。|  
|source|**nvarchar**|ログ エントリを生成したパッケージ内の実行可能ファイルの名前。|  
|sourceid|**uniqueidentifier**|ログ エントリを生成したパッケージ内の実行可能ファイルの GUID。|  
|executionid|**uniqueidentifier**|ログ エントリを生成した実行可能ファイルの実行インスタンスの GUID。|  
|starttime|**datetime**|パッケージの実行が開始された時刻。|  
|endtime|**datetime**|パッケージが完了した時刻。<br /><br /> この機能は実装されていません。 [endtime] 列の値は、[starttime] 列の値と常に同じになります。|  
|datacode|**int**|コンテナーまたはタスクの実行結果を通常示す整数値 (省略可能)。|  
|databytes|**image**|追加情報を格納しているバイト配列 (省略可能)。|  
|message|**nvarchar**|イベントおよびイベントに関連する情報の説明。|  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS & #41;ログ記録](../../integration-services/performance/integration-services-ssis-logging.md)   
  
  
