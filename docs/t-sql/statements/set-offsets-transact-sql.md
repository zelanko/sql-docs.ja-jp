---
title: "セット オフセット (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_OFFSETS_TSQL
- OFFSETS_TSQL
- SET OFFSETS
- OFFSETS
dev_langs:
- TSQL
helpviewer_keywords:
- position relative to start of statement [SQL Server]
- OFFSETS option
- offsets [SQL Server]
- SET OFFSETS statement
ms.assetid: c7bcc697-0930-4630-acae-d8ccbfa4414c
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b0723941708284de7e1489ed9c44f5a3d869f3dd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-offsets-transact-sql"></a>SET OFFSETS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内の指定したキーワードのオフセット (ステートメントの先頭からの相対的な位置) を、DB-Library アプリケーションに返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
 
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SET OFFSETS keyword_list { ON | OFF }  
```  
  
## <a name="arguments"></a>引数  
 *keyword_list*  
 SELECT、FROM、ORDER、TABLE、PROCEDURE、STATEMENT、PARAM、EXECUTE などの [!INCLUDE[tsql](../../includes/tsql-md.md)] 構成要素をコンマで区切って指定します。  
  
## <a name="remarks"></a>解説  
 SET OFFSETS は DB-Library アプリケーションだけで使用されます。  
  
 SET OFFSETS は、実行時ではなく、解析時に設定されます。 解析時に設定されるということは、SET ステートメントがバッチまたはストアド プロシージャ内に指定されている場合、コードが実際にその場所まで実行されるかどうかに関係なく、設定が有効になることを意味します。つまり他のどのステートメントが実行されるよりも前に、SET ステートメントが効力を発するということになります。 たとえば、set ステートメントが場合の場合でもしています.Else ステートメント ブロックに SET ステートメントが指定されていたとしても、IF しています.ELSE ステートメント ブロックは解析されます。  
  
 SET OFFSETS がストアド プロシージャで設定された場合、SET OFFSETS の値は、制御がストアド プロシージャから返された後、元に戻されます。 したがって、動的 SQL に指定されている SET OFFSETS ステートメントは、動的 SQL ステートメントの後にあるステートメントにまったく影響しません。  
  
 OFFSETS オプションが ON でエラーがない場合は、SET PARSEONLY はオフセットを返します。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [[SET parseonly] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-parseonly-transact-sql.md)  
  
  

