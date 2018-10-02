---
title: NULL と UNKNOWN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 9d491846-4730-4740-a680-77c69fae4a58
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7418d7fcfd1fce53a1a95ebaed80c3b306a16b33
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745160"
---
# <a name="null-and-unknown-transact-sql"></a>NULL と UNKNOWN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-pdw-md.md)]

  NULL では、値が不明であることを示します。 Null 値では、空または 0 の値と異なるです。 2 つの NULL 値は等しいとは限りません。 各 NULL の値が不明であるために、2 つの null 値または null 値とその他の値の間の比較は不明な返します。  
  
 Null 値は、通常、不明な適用できないデータを示すか、後で追加します。 たとえば、受注時には顧客のミドル名イニシャルはわかりません。  
  
 Null 値については、次に注意してください。  
  
-   クエリ内で NULL 値を調べるには、WHERE 句で IS NULL または IS NOT NULL を使用します。  
  
-   INSERT または UPDATE ステートメントで NULL を明示的に記述、または INSERT ステートメントからの列にすることで、null 値を列に挿入できます。  
  
-   Null 値は、主キーなど、またはディストリビューション キーなどの行の配信に使用される情報のテーブル内の別の行から、テーブル内の 1 つの行を区別するために必要な情報として使用できません。  
  
 データに NULL 値がある場合、論理演算子と比較演算子は、TRUE や FALSE ではなく UNKNOWN を返すことがあります。 このように 3 つの値を生成する論理は、アプリケーション エラーの原因になります。 UNKNOWN を含むブール式の論理演算子は、演算子の結果が UNKNOWN 式に依存しない限り、UNKNOWN を返します。 この動作の例をまとめたものが次の表です。  
  
 次の表では、1 つの式が UNKNOWN を返す 2 つのブール式に AND 演算子を適用した結果を確認できます。  
  
|式 1|式 2|結果|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|UNKNOWN|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|FALSE|  
  
 次の表では、1 つの式が UNKNOWN を返す 2 つのブール式に OR 演算子を適用した結果を確認できます。  
  
|式 1|式 2|結果|  
|---------------|---------------|------------|  
|TRUE|UNKNOWN|TRUE|  
|UNKNOWN|UNKNOWN|UNKNOWN|  
|FALSE|UNKNOWN|UNKNOWN|  
  
## <a name="see-also"></a>参照  
 [AND &#40;Transact-SQL&#41;](../../t-sql/language-elements/and-transact-sql.md)   
 [OR &#40;Transact-SQL&#41;](../../t-sql/language-elements/or-transact-sql.md)   
 [NOT &#40;Transact-SQL&#41;](../../t-sql/language-elements/not-transact-sql.md)   
 [IS NULL &#40;Transact-SQL&#41;](../../t-sql/queries/is-null-transact-sql.md)  
  
  
