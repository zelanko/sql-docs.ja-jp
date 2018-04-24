---
title: CONNECTIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95c95ad472c5b5d4cb5420fa3b0da8f88053c0c5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

要求が送信された一意の接続の接続プロパティについての情報を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>引数  
*property*  
接続のプロパティです。 *プロパティ* 値は次のいずれかを指定することができます。
  
|ReplTest1|データ型|Description|  
|---|---|---|
|net_transport|**nvarchar(40)**|この接続で使用される物理的な転送プロトコルを返します。 NULL 値は許可されません。<br /><br /> 戻り値は、**HTTP**、**名前付きパイプ**、**セッション**、**共有メモリ**、**SSL**、**CP**、および **VIA** です。<br /><br /> 注: 接続で複数のアクティブな結果セット (MARS) が有効になっているときに、接続プールが有効になっている場合は、常に**セッション**を返します。|  
|protocol_type|**nvarchar(40)**|ペイロードのプロトコルの種類を返します。 現在、TDS (TSQL) と SOAP が区別されます。 NULL 値が許可されます。|  
|auth_scheme|**nvarchar(40)**|接続の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証方法を返します。 認証方法は、Windows 認証 (NTLM、KERBEROS、DIGEST、BASIC、NEGOTIATE) または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のいずれかです。 NULL 値は許可されません。|  
|local_net_address|**varchar(48)**|この接続の対象となったサーバーの IP アドレスを返します。 TCP トランスポート プロバイダーを使用している接続の場合にのみ該当します。 NULL 値が許可されます。|  
|local_tcp_port|**int**|接続が TCP トランスポートを使用している接続であった場合に、この接続の対象となったサーバー TCP ポートを返します。 NULL 値が許可されます。|  
|client_net_address|**varchar(48)**|このサーバーに接続しているクライアントのアドレスを要求します。 NULL 値が許可されます。|  
|physical_net_transport|**nvarchar(40)**|この接続で使用される物理的な転送プロトコルを返します。 接続で複数のアクティブな結果セット (MARS) が有効になっている場合、正確です。|  
|\<その他の文字列>||入力が有効でない場合は、NULL を返します。|  
  
## <a name="remarks"></a>Remarks  
**local_net_address** と **local_tcp_port** で NULL を返す [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。
  
返される値は、[sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) 動的管理ビューの対応する列に表示されるオプションと同じです。 例 :
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>参照
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
