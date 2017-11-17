---
title: "CONNECTIONPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a5b023530bce0269af96918b0d578c6ca54293d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
*プロパティ*  
接続のプロパティです。 *プロパティ*値は次のいずれかになります。
  
|値|データ型|Description|  
|---|---|---|
|net_transport|**nvarchar (40)**|この接続で使用される物理的な転送プロトコルを返します。 NULL 値は許可されません。<br /><br /> 戻り値は、: **HTTP**、**名前付きパイプ**、**セッション**、**共有メモリ**、 **SSL**、 **TCP**、および**VIA**です。<br /><br /> 注: 常に返します**セッション**との接続が有効にすると、複数のアクティブな結果セット (MARS)、接続プールが有効にします。|  
|protocol_type|**nvarchar (40)**|ペイロードのプロトコルの種類を返します。 現在、TDS (TSQL) と SOAP が区別されます。 NULL 値が許可されます。|  
|auth_scheme|**nvarchar (40)**|返します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続の認証スキームです。 認証方法は、いずれかの Windows 認証 (NTLM、KERBEROS、DIGEST、BASIC、NEGOTIATE) または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。 NULL 値は許可されません。|  
|local_net_address|**varchar(48)**|この接続の対象となったサーバーの IP アドレスを返します。 TCP トランスポート プロバイダーを使用している接続の場合にのみ該当します。 NULL 値が許可されます。|  
|local_tcp_port|**int**|接続が TCP トランスポートを使用している接続であった場合に、この接続の対象となったサーバー TCP ポートを返します。 NULL 値が許可されます。|  
|client_net_address|**varchar(48)**|このサーバーに接続しているクライアントのアドレスを要求します。 NULL 値が許可されます。|  
|physical_net_transport|**nvarchar (40)**|この接続で使用される物理的な転送プロトコルを返します。 接続で複数のアクティブな結果セット (MARS) が有効になっている場合、正確です。|  
|\<その他の文字列 >||入力が有効でない場合は、NULL を返します。|  
  
## <a name="remarks"></a>解説  
**local_net_address**と**local_tcp_port**で NULL を返す[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。
  
返される値は、対応する列の表示されるオプションと同じ、 [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md)動的管理ビュー。 例:
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>参照
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  

