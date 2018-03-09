---
title: "sys.fn_virtualservernodes (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_virtualservernodes
- fn_virtualservernodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- nodes [Faillover Clustering], virtual servers
- nodes [Faillover Clustering]
- virtual servers [Faillover Clustering]
- failover clustering [SQL Server], nodes
- fn_virtualservernodes function
- sys.fn_virtualservernodes function
ms.assetid: 257f3b8d-93c0-4444-87f1-ea211bd8cad0
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 918966abed033f139e666922ff3835140feea981
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="sysfnvirtualservernodes-transact-sql"></a>sys.fn_virtualservernodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  これでフェールオーバー クラスター インスタンス ノードの一覧を返しますのインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行できます。 この情報は、フェールオーバー クラスタリング環境で役立ちます。  
  
> [!IMPORTANT]  
>  これは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]システム関数は下位互換性のために含まれます。 使用することをお勧め[sys.dm_os_cluster_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_virtualservernodes()  
```  
  
## <a name="tables-returned"></a>返されたテーブル  
 現在のサーバーが、クラスター化されたサーバーの場合**fn_virtualservernodes**このフェールオーバー クラスター インスタンス ノードの一覧を返しますのインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は定義されています。  
  
 現在のサーバー インスタンスが、クラスター化されたサーバーではない場合**fn_virtualservernodes**空の行セットを返します。  
  
## <a name="permissions"></a>権限  
 ユーザーがのインスタンスの VIEW SERVER STATE 権限を持つ必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="examples"></a>使用例  
 次の例では`fn_virtualservernodes`クラスター化されたサーバー インスタンスに対してクエリを実行します。  
  
```  
SELECT * FROM fn_virtualservernodes();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 NodeName  
  
 -------\-  
  
 SS3-CLUSN1  
  
 SS3-CLUSN2  
  
## <a name="see-also"></a>参照  
 [sys.dm_os_cluster_nodes &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.fn_servershareddrives &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)  
  
  
