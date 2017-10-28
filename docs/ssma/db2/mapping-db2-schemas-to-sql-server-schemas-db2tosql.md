---
title: "DB2 スキーマをマッピングから SQL Server スキーマ (DB2ToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 5d4d96ee2d2fb0bad8947b85c36ef6b27f4af326
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>SQL Server スキーマ (DB2ToSQL) への DB2 スキーマのマッピング
DB2 の場合に、各データベースは、1 つまたは複数のスキーマを持っています。 既定では、SSMA は DB2 スキーマ内のすべてのオブジェクトを移行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマという名前のデータベースです。 ただし、DB2 スキーマ間のマッピングをカスタマイズすることができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="db2-and-sql-server-schemas"></a>DB2 および SQL Server スキーマ  
DB2 データベースには、スキーマが含まれています。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]それぞれが複数のスキーマを持つことができます、複数のデータベースが含まれています。  
  
DB2 の概念スキーマのマップ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースとそのスキーマのいずれかの概念です。 たとえば、DB2 がという名前のスキーマを含めることが**HR**です。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]という名前のデータベースがあります**HR**は、そのデータベース内のスキーマです。 1 つのスキーマは、 **dbo** (またはデータベース所有者) スキーマ。 既定では、DB2 スキーマ**HR**にマップされます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマ**HR.dbo**です。 SSMA を指す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマとしてデータベースおよびスキーマの組み合わせ。  
  
DB2 の間のマッピングを変更して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマです。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA で、使用可能なに DB2 スキーマをマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマです。  
  
**データベースおよびスキーマを変更するには**  
  
1.  DB2 メタデータ エクスプ ローラーで、次のように選択します。**スキーマ**です。  
  
    **スキーマ マッピング** タブは、個々 のデータベースを選択した場合にも使用可能な**スキーマ**フォルダー、または個別のスキーマです。 一覧で、**スキーマ マッピング** タブを選択したオブジェクトのカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブです。  
  
    対象の値が続くすべての DB2 スキーマの一覧が表示されます。 このターゲットは、2 部構成の表記法で表されます (*database.schema*) で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクトとデータを移行します。  
  
3.  選択を行い、をクリックするマッピングを含む行**変更**です。  
  
    **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能な対象データベースとスキーマ、または型データベースおよびスキーマで 2 部構成の表記 (database.schema) で、テキスト ボックスの名前をクリックを参照することがあります**OK**です。  
  
4.  は、ターゲットの変更、**スキーマ マッピング**タブです。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベースです。 マップされているターゲット データベースが存在しないで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージを使用するように求められますが、 **"データベースまたはスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。か続行しますか?"** [はい] をクリックします。 同様に、[ターゲット] で、存在しないスキーマをスキーマをマップできる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマを元に戻す  
DB2 スキーマ間のマッピングをカスタマイズする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマ、既定値に戻すマッピングを戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  スキーマのマッピング] タブで、[任意の行を選択し、をクリックして**既定値にリセット**既定のデータベースとスキーマを元に戻す。  
  
## <a name="next-steps"></a>次の手順  
DB2 オブジェクトへの変換を分析するかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト、することができます[データ移行レポート (SSMA 共通)](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)です。  
  
## <a name="see-also"></a>参照  
[SQL Server (&) #40";"DB2eToSQL"&"#41; への接続](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[SQL Server (&) #40";"DB2ToSQL"&"#41; への DB2 データベースの移行](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  

