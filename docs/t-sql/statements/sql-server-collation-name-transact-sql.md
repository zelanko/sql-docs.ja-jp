---
title: "SQL Server 照合順序名 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7265f4efe0d790ab61e4e522af83d6b91b710a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-collation-name-transact-sql"></a>SQL Server 照合順序名 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つの文字列の照合順序名を指定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]照合順序。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows 照合順序をサポートしています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]限られた数をサポート (< 80) と呼ばれる照合順序の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]照合順序の前に開発された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows 照合順序をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]照合順序は旧バージョンと互換性のため、引き続きサポートされますが、新しい開発作業では使用できません。 Windows 照合順序の詳細については、次を参照してください。 [Windows 照合順序名 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
<SQL_collation_name> :: =   
SQL_SortRules[_Pref]_CPCodepage_<ComparisonStyle>  
  
<ComparisonStyle> ::=  
_CaseSensitivity_AccentSensitivity | _BIN  
```  
  
## <a name="arguments"></a>引数  
 *SortRules*  
 辞書順での並べ替えを指定した場合に適用される、並べ替え規則を持つアルファベットまたは言語を示す文字列です。 たとえば、Latin1_General や Polish を指定します。  
  
 **基本設定**  
 大文字優先を指定します。 場合でも、大文字と小文字の比較は、その他の区別がない場合に小文字のバージョンでは、前に、文字の大文字バージョンを並べ替えます。  
  
 *Codepage*  
 照合順序で使用されるコード ページを識別する 1 ～ 4 桁の番号を指定します。 **CP1**の他のすべてのコード ページの完全なコード ページ番号が指定されている、コード ページ 1252 を指定します。 たとえば、 **CP1251**コード ページ 1251 を指定し、 **CP850**コード ページ 850 を指定します。  
  
 *CaseSensitivity*  
 **CI**区別されず、指定**CS**大文字小文字を区別を指定します。  
  
 *AccentSensitivity*  
 **AI**アクセントを区別しない指定**AS**アクセントを区別を指定します。  
  
 **箱**  
 使用するバイナリ並べ替え順を指定します。  
  
## <a name="remarks"></a>解説  
 一覧に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サーバーによってサポートされる照合順序は、次のクエリを実行します。  
  
```  
SELECT * FROM sys.fn_helpcollations()   
WHERE name LIKE 'SQL%';  
```  

>  [!NOTE]  
>  並べ替え順 ID 80 では、任意の Window 照合順序コード ページ 1250 およびバイナリ順を使用します。 たとえば、Albanian_BIN、Croatian_BIN、Czech_BIN、Romanian_BIN、Slovak_BIN、Slovenian_BIN を使用します。  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [定数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [テーブルと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  

