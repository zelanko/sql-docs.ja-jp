---
title: "GET_TRANSMISSION_STATUS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATUS_TSQL
- TRANSMISSION
- TRANSMISSION_TSQL
- GET_TRANSMISSION_STATUS
- STATUS
- GET_TRANSMISSION_STATUS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], transmission status
- Service Broker errors, transmission status
- transmission status information
- status information [SQL Server], conversations
- GET_TRANSMISSION_STATUS statement
ms.assetid: 621805d5-49ed-4764-b3cb-2ae4a3bf797e
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b6d5152cca3f4ddb1afe0d8042c84743c31abf9b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="gettransmissionstatus-transact-sql"></a>GET_TRANSMISSION_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メッセージ交換の一方の側に関して、最後の転送の状態を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
GET_TRANSMISSION_STATUS ( conversation_handle )  
```  
  
## <a name="arguments"></a>引数  
 *conversation_id*  
 メッセージ交換で使用するメッセージ交換ハンドルを指定します。 このパラメーターの型は**uniqueidentifier**です。  
  
## <a name="return-types"></a>戻り値の型  
 **nchar**  
  
## <a name="remarks"></a>解説  
 指定したメッセージ交換に関する、最後の転送試行の状態を説明する文字列を返します。 最後の送信の試行が成功した場合、送信の試行がまだ行われていない場合、または場合に、空の文字列を返します、 *conversation_handle*存在しません。  
  
 この関数で返される情報は、管理ビュー sys.transmission_queue の last_transmission_error 列で表示される情報と同じです。 ただし、この関数を使用すると、転送キューに現在メッセージがないメッセージ交換の転送状態を検出できます。  
  
> [!NOTE]  
>  GET_TRANSMISSION_STATUS では、現在のインスタンスにメッセージ交換エンドポイントを持たないメッセージの情報は提供されません。 つまり、転送されるメッセージの情報は使用できません。  
  
## <a name="examples"></a>使用例  
 次の例では、メッセージ交換ハンドル `58ef1d2d-c405-42eb-a762-23ff320bddf0` とのメッセージ交換に関する転送状態がレポートされます。  
  
```  
SELECT Status =  
    GET_TRANSMISSION_STATUS('58ef1d2d-c405-42eb-a762-23ff320bddf0') ;  
```  
  
 行の長さの編集、サンプルの結果セットを次に示します。  
  
 ```
 Status  
 ------------------------------- 
 The Service Broker protocol transport is disabled or not configured.
 ```  
  
 この場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が使用できるように構成されていない[!INCLUDE[ssSB](../../includes/sssb-md.md)]ネットワーク経由で通信するためにします。  
  
## <a name="see-also"></a>参照  
 [sys.conversation_endpoints & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)   
 [sys.transmission_queue & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  

