---
title: "SET ANSI_DEFAULTS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET ANSI_DEFAULTS
- ANSI_DEFAULTS
- SET_ANSI_DEFAULTS_TSQL
- ANSI_DEFAULTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ANSI_DEFAULTS option
- SET ANSI_DEFAULTS statement
ms.assetid: bd721d97-6e23-488b-8c8c-c0453d5b3b86
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 170fb1f5a95b9f6fe4fbe596906595475175b1a2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansidefaults-transact-sql"></a>SET ANSI_DEFAULTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  一部の ISO 標準動作を集合的に指定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設定のグループを制御します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_DEFAULTS { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_DEFAULTS ON;  
```  
  
## <a name="remarks"></a>解説  
 SET ANSI_DEFAULTS は、クライアントで変更できない、サーバー側の設定です。 クライアントは自身の設定を管理します。 既定では、クライアントの設定はサーバー設定と対照的です。 サーバー設定は、ユーザーが変更するものではありません。 ユーザーがクライアントの動作を変更するには、SQL_COPT_SS_PRESERVE_CURSORS を使用します。 詳細については、次を参照してください。 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)です。  
  
 有効 (ON) に設定すると、次の ISO 設定が有効になります。  
  
|||  
|-|-|  
|[SET ANSI_NULLS]|[SET CURSOR_CLOSE_ON_COMMIT]|  
|[SET ANSI_NULL_DFLT_ON]|[SET IMPLICIT_TRANSACTIONS]|  
|[SET ANSI_PADDING]|[SET QUOTED_IDENTIFIER]|  
|[SET ANSI_WARNINGS]||  
  
 また、ユーザーの作業セッション時や、トリガーまたはストアド プロシージャの実行時は、これらの ISO 標準 SET オプションは、クエリ処理環境を定義します。 ただし、これらの SET オプションには ISO 標準に準拠するために必要なオプションがすべて含まれているわけではありません。  
  
 計算列およびインデックス付きビューにおいてインデックスを操作する場合は、4 つの既定オプション (ANSI_NULLS、ANSI_PADDING、ANSI_WARNINGS、および QUOTED_IDENTIFIER) を ON に設定する必要があります。 これは、計算列とインデックス付きビューにおいてインデックスを作成および変更するときに、指定された値に設定する必要がある 7 つの SET オプションの中の 4 つのオプションです。 その他の SET オプションは、ARITHABORT (ON)、CONCAT_NULL_YIELDS_NULL (ON)、および NUMERIC_ROUNDABORT (OFF) です。 計算列でインデックス付きビューとインデックスで必要な SET オプション設定に関する詳細についてを参照してください「の考慮事項とする SET ステートメントの使用」 [SET ステートメント & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statements-transact-sql.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するときに、ON に ANSI_DEFAULTS を自動的に設定します。 次に、このドライバーとプロバイダーは、CURSOR_CLOSE_ON_COMMIT と IMPLICIT_TRANSACTIONS を OFF に設定します。 ODBC データ ソース、ODBC 接続属性、またはに接続する前に、アプリケーションで設定されている OLE DB 接続プロパティでは、SET CURSOR_CLOSE_ON_COMMIT と SET IMPLICIT_TRANSACTIONS OFF 設定を構成することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 DB-Library アプリケーションからの接続に対しては、SET ANSI_DEFAULTS は既定で OFF に設定されています。  
  
 SET ANSI_DEFAULTS を実行すると、SET QUOTED_IDENTIFIER は解析時に設定され、次のオプションは実行時に設定されます。  
  
|||  
|-|-|  
|[SET ANSI_NULLS]|[SET ANSI_WARNINGS]|  
|[SET ANSI_NULL_DFLT_ON]|[SET CURSOR_CLOSE_ON_COMMIT]|  
|[SET ANSI_PADDING]|[SET IMPLICIT_TRANSACTIONS]|  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`SET ANSI_DEFAULTS ON` を設定し、`DBCC USEROPTIONS` ステートメントを使用して、影響を受ける設定を表示します。  
  
```  
-- SET ANSI_DEFAULTS ON.  
SET ANSI_DEFAULTS ON;  
GO  
-- Display the current settings.  
DBCC USEROPTIONS;  
GO  
-- SET ANSI_DEFAULTS OFF.  
SET ANSI_DEFAULTS OFF;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DBCC USEROPTIONS & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-useroptions-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [セット ANSI_NULL_DFLT_ON & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)   
 [[SET cursor_close_on_commit] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-cursor-close-on-commit-transact-sql.md)   
 [[SET implicit_transactions] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md)  
  
  

