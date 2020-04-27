---
title: dm_os_child_instances (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 59a58348f5428f568f40d28b4e83bc6bc040647c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900233"
---
# <a name="sysdm_os_child_instances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  親サーバーインスタンスから作成されたユーザーインスタンスごとに1行の値を返します。  
  
> **重要:** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 **Dm_os_child_instances**から返された情報を使用して、各ユーザーインスタンス (heart_beat) の状態を判断し、または SQLCmd を使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ユーザーインスタンスへの接続を作成するために使用できるパイプ名 (instance_pipe_name) を取得できます。 ユーザーインスタンスに接続できるのは、クライアントアプリケーションなどの外部プロセスによって開始された後だけです。 SQL 管理ツールはユーザーインスタンスを開始できません。  
  
> **注:** ユーザーインスタンスは、の[!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)]機能です。  
> 
> **メモ**またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_os_child_instances**という名前を使用します。  
  
|列|データ型|説明|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar(256)**|このユーザーインスタンスが作成されたユーザーの名前。|  
|owning_principal_sid|nvarchar(256)|このユーザーインスタンスを所有するプリンシパルの SID (セキュリティ識別子)。 この値は、Windows SID と一致します。|  
|owning_principal_sid_binary|varbinary(85)|ユーザーインスタンスを所有するユーザーの SID のバイナリバージョン|  
|**instance_name**|**nvarchar(128)**|このユーザーインスタンスの名前。|  
|**instance_pipe_name**|**nvarchar(260)**|ユーザー インスタンスを作成すると、アプリケーションから接続するための名前付きパイプが作成されます。 この名前は、このユーザーインスタンスに接続するために接続文字列で使用できます。|  
|**os_process_id**|**Int**|このユーザーインスタンスの Windows プロセスのプロセス番号。|  
|**os_process_creation_date**|**/**|このユーザー インスタンス プロセスの前回の開始日付と時刻です。|  
|**heart_beat**|**nvarchar (5)**|このユーザー インスタンスの現在の状態 (ALIVE または DEAD) です。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>Remarks  
 動的管理ビューの詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「[動的管理ビューと関数 &#40;transact-sql&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [管理者以外のユーザーのためのユーザー インスタンス](https://msdn.microsoft.com/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



