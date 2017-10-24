---
title: "SET FIPS_FLAGGER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FIPS_FLAGGER
- SET_FIPS_FLAGGER_TSQL
- FIPS_FLAGGER_TSQL
- SET FIPS_FLAGGER
dev_langs:
- TSQL
helpviewer_keywords:
- SET FIPS_FLAGGER statement
- FIPS 127-2 standard
- FIPS_FLAGGER option
ms.assetid: e82f6bee-6cf6-4061-be22-9ad2e8e9d3d6
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4c28fd5419aec8bf15745150288b6878fd65ac1f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-fipsflagger-transact-sql"></a>SET FIPS_FLAGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  FIPS 127-2 標準に準拠しているかどうかをチェックします。 これは ISO 標準を基準にしています。 SQL Server の FIPS 準拠については、次を参照してください。 [FIPS 140-2 準拠モードで SQL Server 2016 の使用方法](https://support.microsoft.com/help/4014354/how-to-use-sql-server-2016-in-fips-140-2-compliant-mode)です。 
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SET FIPS_FLAGGER ( 'level' |  OFF )  
```  
  
## <a name="arguments"></a>引数  
 **'** *レベル* **'**  
 FIPS 127-2 標準に対してすべてのデータベース操作の準拠性をチェックするレベルを指定します。 データベースの操作を選択すると、ISO 標準のレベルと競合する場合[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]警告が生成されます。  
  
 *レベル*値は次のいずれかを指定する必要があります。  
  
|値|Description|  
|-----------|-----------------|  
|ENTRY|ISO エントリレベルの準拠性の標準チェック|  
|FULL|ISO 完全準拠性の標準チェック|  
|INTERMEDIATE|ISO 中間レベルの準拠性の標準チェック|  
|OFF|標準チェックなし|  
  
## <a name="remarks"></a>解説  
 設定は、`SET FIPS_FLAGGER`ではなく解析時に設定または実行時に。 解析時に設定を意味する SET ステートメントがバッチまたはストアド プロシージャに存在する場合は、有効になります、その場所が実際にまでコードが実行されるかどうかに関係なくおよび`SET`ステートメントが実行される前に、ステートメントは有効です。 などの場合であっても、`SET`ステートメントが、`IF...ELSE`決して到達しない場合、実行中にステートメント ブロック、`SET`ステートメントも反映ため、`IF...ELSE`ステートメント ブロックを解析します。  
  
 場合`SET FIPS_FLAGGER`ストアド プロシージャでの値に設定されている`SET FIPS_FLAGGER`制御がストアド プロシージャから返された後に復元します。 したがって、`SET FIPS_FLAGGER`動的 SQL で指定されたステートメントには、動的 SQL ステートメントに続くステートメントには影響はありません。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

