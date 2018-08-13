---
title: sys.fn_check_object_signatures (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fn_check_object_signatures_TSQL
- fn_check_object_signatures_TSQL
- fn_check_object_signatures
- sys.fn_check_object_signatures
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_check_object_signatures function
ms.assetid: 47509566-d3d7-46a9-89c1-91b4895d56b9
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 9ed5b999619de7958d0ca180b6e2bdd1a2b14283
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39544862"
---
# <a name="sysfncheckobjectsignatures-transact-sql"></a>sys.fn_check_object_signatures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  署名可能なすべてのオブジェクトの一覧を返し、オブジェクトが、指定した証明書または非対称キーで署名されているかどうかを示します。 オブジェクトが、指定した証明書または非対称キーで署名されている場合は、そのオブジェクトの署名が有効かどうかも返します。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
fn_ check_object_signatures (   
    { '@class' } , { @thumbprint }   
  )   
```  
  
## <a name="arguments"></a>引数  
 {0} '\@*クラス*'}  
 提供される拇印の種類を特定します。  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 \@*クラス*は**sysname**します。  
  
 { \@*拇印*}  
 キーの暗号化で使用された証明書の SHA-1 ハッシュ。または、キーの暗号化で使用された非対称キーの GUID。 \@*拇印*は**varbinary (20)** します。  
  
## <a name="tables-returned"></a>返されるテーブル  
 次の表に、列を**fn_check_object_signatures**を返します。  
  
|[列]|型|説明|  
|------------|----------|-----------------|  
|type|**nvarchar(120)**|種類の説明またはアセンブリを返します。|  
|entity_id|**int**|評価対象のオブジェクトのオブジェクト ID を返します。|  
|is_signed|**int**|提供された拇印でオブジェクトが署名されていない場合は 0 を返します。 提供された拇印でオブジェクトが署名されている場合は 1 を返します。|  
|is_signature_valid|**int**|is_signed の値が 1 の場合、署名が有効ではないときは 0 を返します。 署名が有効であるときは 1 を返します。<br /><br /> is_signed の値が 0 の場合は、常に 0 を返します。|  
  
## <a name="remarks"></a>コメント  
 使用**fn_check_object_signatures**を悪意のあるユーザーがオブジェクトに改ざんされていないことを確認します。  
  
## <a name="permissions"></a>アクセス許可  
 証明書または非対称キーに対する VIEW DEFINITION 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、署名証明書のスキーマを検索、`master`データベース、および返します、 `is_signed` 1 の値と`is_signature_valid`スキーマ署名証明書によって署名されていると、有効になったこれらのオブジェクトの 1 の値署名します。  
  
```  
USE master;  
-- Declare a variable to hold the thumbprint.  
DECLARE @thumbprint varbinary(20) ;  
-- Populate the thumbprint variable with the master database schema signing certificate.  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%' ;  
-- Evaluates the objects signed by the schema signing certificate  
SELECT type, entity_id, OBJECT_NAME(entity_id) AS [object name], is_signed, is_signature_valid  
FROM sys.fn_check_object_signatures ('certificate', @thumbprint) ;  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [IS_OBJECTSIGNED &#40;TRANSACT-SQL&#41;](../../t-sql/functions/is-objectsigned-transact-sql.md)  
  
  
