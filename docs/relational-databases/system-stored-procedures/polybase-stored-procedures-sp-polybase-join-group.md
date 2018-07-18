---
title: sp_polybase_join_group |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sp_polybase_join_group
helpviewer_keywords:
- PolyBase
ms.assetid: 48066431-fed2-4a8a-85af-ac704689e183
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 927c07456401bf441e3ad6491111bad6c85e3c19
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38037780"
---
# <a name="sppolybasejoingroup-transact-sql"></a>sp_polybase_join_group (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  スケール アウト計算 PolyBase グループに、コンピューティング ノードとして、SQL Server インスタンスを追加します。  
  
 SQL Server インスタンスが必要、 [PolyBase](../../relational-databases/polybase/polybase-guide.md)機能をインストールします。  PolyBase では、Hadoop と Azure blob ストレージなどの SQL Server 以外のデータ ソースの統合を使用できます。 参照してください[sp_polybase_leave_group &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md)します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>引数  
 *@head_node_address* = N'*head_node_address*'  
 PolyBase スケール アウトのグループの SQL Server のヘッド ノードをホストしているコンピューターの名前。 *@head_node_address* nvarchar (255) です。  
  
 *@dms_control_channel_port* dms_control_channel_port を =  
 ヘッド ノード PolyBase データ移動のサービスのコントロール チャネルを実行しているポートです。 *@dms_control_channel_port* 符号なしの _ _int16 です。 既定値は**16450**します。  
  
 *@head_node_sql_server_instance_name* head_node_sql_server_instance_name を =  
 PolyBase スケール アウトのグループ内のヘッド ノードの SQL Server インスタンスの名前です。 *@head_node_sql_server_instance_name* nvarchar (16) です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 ストアド プロシージャを実行すた後には、PolyBase エンジンのシャット ダウンし、マシン上のサービスを PolyBase データの移動を再起動します。 確認するヘッド ノードで次の DMV を実行する: **sys.dm_exec_compute_nodes**します。  
  
## <a name="example"></a>例  
 例では、PolyBase グループにコンピューティング ノードとして、現在のコンピューターを結合します。  ヘッド ノードの名前は**HST01**ヘッド ノード上の SQL Server インスタンスの名前が、 **MSSQLSERVER**します。  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>参照  
 [PolyBase の概要](../../relational-databases/polybase/get-started-with-polybase.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
