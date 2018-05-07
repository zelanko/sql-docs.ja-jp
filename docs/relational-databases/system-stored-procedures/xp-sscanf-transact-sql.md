---
title: xp_sscanf (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_sscanf_TSQL
- xp_sscanf
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sscanf
ms.assetid: 619a9df1-7008-407e-a75a-bc6f851454a8
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b989dfa254330034cab4ab5278e2e4a9cca4da3d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xpsscanf-transact-sql"></a>xp_sscanf (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  文字列からのデータを、それぞれのフォーマット引数によって与えられる引数の位置に読み込みます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
xp_sscanf { string OUTPUT , format } [ ,argument [ ,...n ] ]   
```  
  
## <a name="arguments"></a>引数  
 **文字列**  
 引数の値を読み出す文字列を指定します。  
  
 OUTPUT  
 値を指定した場合、配置*引数*出力パラメーターです。  
  
 *format*  
 書式設定された文字列がに似ていますが、C 言語のサポート内容**sscanf**関数。 現在サポートしているのは %s フォーマット引数のみです。  
  
 *argument*  
 **Varchar**変数の対応する値に設定*形式*引数。  
  
 *n*  
 最大 50 の引数を指定できることを示すプレースホルダーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 **xp_sscanf**次のメッセージが返されます。  
  
 `Command(s) completed successfully.`  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`xp_sscanf` を使用して、ソース文字列のフォーマットにおけるそれぞれの位置に基づいて、ソース文字列から 2 つの値を抽出します。  
  
```  
DECLARE @filename varchar (20), @message varchar (20);  
EXEC xp_sscanf 'sync -b -fproducts10.tmp -rrandom', 'sync -b -f%s -r%s',   
  @filename OUTPUT, @message OUTPUT;  
SELECT @filename, @message;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------------- --------------------   
products10.tmp        random  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [汎用拡張ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_sprintf &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/xp-sprintf-transact-sql.md)  
  
  
