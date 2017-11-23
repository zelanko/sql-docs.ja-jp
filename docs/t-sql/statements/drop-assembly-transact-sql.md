---
title: "ドロップ アセンブリ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ASSEMBLY
- DROP_ASSEMBLY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- deleting assemblies
- assemblies [CLR integration], removing
- dropping assemblies
- WITH NO DEPENDENTS option
ms.assetid: 452d181a-a8e6-44a3-975d-29966d01b18d
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e466c9be38de4706493f3d181ca1648c9027a19
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="drop-assembly-transact-sql"></a>DROP ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースから、アセンブリとそれに関連するすべてのファイルを削除します。 アセンブリを使用して作成される[CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md)を使用して変更および[ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP ASSEMBLY [ IF EXISTS ] assembly_name [ ,...n ]  
[ WITH NO DEPENDENTS ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、アセンブリを削除します。  
  
 *アセンブリ名*  
 削除するアセンブリの名前を指定します。  
  
 WITH NO DEPENDENTS  
 指定した場合のみ削除*アセンブリ名*アセンブリによって参照される依存アセンブリの"なし"です。 指定しない場合、DROP ASSEMBLY は削除*assembly_name*とすべての依存アセンブリです。  
  
## <a name="remarks"></a>解説  
 アセンブリを削除すると、ソース コードやデバッグ ファイルなど、アセンブリに関連するファイルもデータベースから削除されます。  
  
 WITH NO DEPENDENTS が指定されていない場合に、DROP ASSEMBLY が切断*assembly_name*とすべての依存アセンブリです。 依存アセンブリの削除に失敗した場合、DROP ASSEMBLY ではエラーが返されます。  
  
 アセンブリが、データベースに存在する他のアセンブリによって参照されているか、現在のデータベースの共通言語ランタイム (CLR) 関数、プロシージャ、トリガー、ユーザー定義型、または集計で使用されている場合、DROP ASSEMBLY ではエラーが返されます。  
  
 DROP ASSEMBLY は、アセンブリを参照する現在実行中のコードには影響を与えません。 ただし、DROP ASSEMBLY を実行した後では、アセンブリ コードの呼び出しは失敗します。  
  
## <a name="permissions"></a>Permissions  
 アセンブリの所有権、またはアセンブリに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、アセンブリ`HelloWorld`のインスタンスで既に作成されて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
DROP ASSEMBLY Helloworld ;  
```  
  
## <a name="see-also"></a>参照  
 [アセンブリ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-assembly-transact-sql.md)   
 [アセンブリの変更 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [アセンブリに関する情報の取得](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
