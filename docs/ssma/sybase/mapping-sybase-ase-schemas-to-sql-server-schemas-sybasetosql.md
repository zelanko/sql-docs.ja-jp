---
title: "SQL Server スキーマ (SybaseToSQL) にマッピング Sybase ASE スキーマ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords: Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 98b90bb9b511af631f7ae27d969df21576ca6502
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>SQL Server スキーマ (SybaseToSQL) にマッピング Sybase ASE スキーマ
Sybase Adaptive Server Enterprise (ASE)、各データベースは、1 つまたは複数のスキーマを持っています。 既定では、SSMA は、同じデータベースおよびスキーマ内にデータベースおよびスキーマ内のすべてのオブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 ただし、ASE 間のマッピングをカスタマイズすることができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースとスキーマです。  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE と SQL Server または SQL Azure スキーマ  
ASE と[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure として 2 つのパーツ表記を使用してデータベースおよびそのスキーマを指定または*database.schema*です。 ASE 内にはたとえば、**デモ**データベースである可能性があります、 **dbo**スキーマです。 データベースとスキーマのペアとして指定されている**demo.dbo**です。 場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure は、同じデータベースおよびスキーマは、ペアも指定されてとして**demo.dbo**です。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA をマップする ASE スキーマに、使用可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のスキーマです。  
  
**データベースおよびスキーマを変更するには**  
  
1.  Sybase メタデータ エクスプ ローラーで、次のように選択します。**データベース**です。  
  
    **スキーマ マッピング** タブは、個々 のデータベースを選択した場合にも使用可能な**スキーマ**フォルダー、または個別のスキーマです。 一覧で、**スキーマ マッピング** タブを選択したオブジェクトのカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブです。  
  
    対象の値を続けて、そのスキーマを持つすべての ASE データベースの一覧が表示されます。 このターゲットは、2 部構成の表記法で表されます (*database.schema*) で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のオブジェクトとデータを移行します。  
  
3.  選択を行い、をクリックするマッピングを含む行**変更**です。  
  
4.  **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能な対象データベースとスキーマ、または型データベースおよびスキーマで 2 部構成の表記 (database.schema) で、テキスト ボックスの名前をクリックを参照することがあります**OK**です。  
  
5.  は、ターゲットの変更、**スキーマ マッピング**タブです。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベースです。 マップされているターゲット データベースが存在しないで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージを使用するように求められますが、 **"データベースまたはスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。か続行しますか?"** [はい] をクリックします。 同様に、[ターゲット] で、存在しないスキーマをスキーマをマップできる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
-   SQL Azure へのマッピング  
  
接続されているターゲット SQL Azure データベースへ、または接続されているターゲット SQL Azure データベース内の任意のスキーマには、ソース データベースをマップできます。 ソース スキーマ 接続されているターゲット データベースの任意の存在しないスキーマをマップするかどうかは、メッセージが求められます**"スキーマが対象のメタデータには存在できません。これが同期中に作成されます。続行しますか?"**はい をクリックします。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマを元に戻す  
ASE スキーマ間のマッピングをカスタマイズする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のスキーマを既定値に戻して、マッピングを戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  スキーマのマッピング] タブで、[任意の行を選択し、をクリックして**既定値にリセット**既定のデータベースとスキーマを元に戻す。  
  
## <a name="next-steps"></a>次の手順  
Sybase ASE オブジェクトへの変換を分析するかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトを実行できます[変換レポートを作成する](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c)です。 それ以外の場合を実行できます[ASE データベース オブジェクトの定義の変換](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3)に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトの定義。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
