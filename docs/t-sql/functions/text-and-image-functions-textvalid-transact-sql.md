---
title: "TEXTVALID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 279022316af7e3a396c7089f48933281264f900f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>テキストとイメージ関数 - TEXTVALID (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  A**テキスト**、 **ntext**、または**イメージ**関数を特定のテキスト ポインターが有効かどうかを確認します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代替機能は使用できません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
## <a name="arguments"></a>引数  
 *テーブル*  
 使用するテーブルの名前です。  
  
 *列*  
 使用する列の名前です。  
  
 *text_ptr*  
 確認するテキスト ポインターです。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 ポインターが有効なら 1 を、ポインターが無効なら 0 を返します。 なおの識別子、**テキスト**列は、テーブル名を含める必要があります。 有効なテキスト ポインターがないと、UPDATETEXT、WRITETEXT、READTEXT は使用できません。  
  
 次の関数とステートメントも役立ちますを操作するときに**テキスト**、 **ntext**、および**イメージ**データ。  
  
|関数またはステートメント|Description|  
|---------------------------|-----------------|  
|PATINDEX**(**'*パターンを %**'***、** *式***)**|指定された文字列内の文字位置を返します**テキスト**と**ntext**列です。|  
|DATALENGTH**(***式***)**|内のデータの長さを返します**テキスト**、 **ntext**、および**イメージ**列です。|  
|[SET TEXTSIZE]|制限 (バイト単位) を返します、**テキスト**、 **ntext**、または**イメージ**は SELECT ステートメントで返されるデータ。|  
  
## <a name="examples"></a>使用例  
 次の例のレポート内の各値の有効なテキスト ポインターが存在するかどうか、`logo`の列、`pub_info`テーブル。  
  
> [!NOTE]  
>  この例を実行するにインストールする必要があります、 **pubs**データベース。  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [DATALENGTH & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/patindex-transact-sql.md)   
 [[SET textsize] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-textsize-transact-sql.md)   
 [テキストとイメージ関数 & #40 です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  

