---
title: MySQL データベースを SQL Server スキーマ (MySQLToSQL) にマッピング |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9ad7ad2647e0f1c9c6145d3277c1bee911fdcde9
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776718"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>MySQL データベースを SQL Server スキーマ (MySQLToSQL) にマッピング
SSMA for MySQL は既定では、MySQL スキーマ内のすべてのオブジェクトを移行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースのスキーマの名前します。 ただし、MySQL スキーマ間のマッピングをカスタマイズすることができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベース。  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL および SQL Server または SQL Azure スキーマ  
スキーマの MySQL 概念は、データベースとそのスキーマの 1 つの SQL Server 概念にマップされます。 SSMA は、SQL Server とを組み合わせたデータベース スキーマとしてスキーマを参照します。  
  
スキーマの MySQL 概念は、データベースとそのスキーマの 1 つの SQL Server 概念にマップされます。 たとえば、MySQL がという名前のスキーマを含めることが**HR**です。 SQL Server のインスタンスは、という名前のデータベースを持つ可能性があります**HR**は、そのデータベース内のスキーマです。 1 つのスキーマは、 **dbo** (またはデータベース所有者) スキーマ。 既定では、MySQL スキーマ**HR**にマップされます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマ**HR.dbo**です。 SSMA を指す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマとしてデータベースおよびスキーマの組み合わせ。  
  
MySQL の間のマッピングを変更して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure のスキーマです。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA をマップする MySQL スキーマを使用可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のスキーマです。  
  
**データベースおよびスキーマを変更するには**  
  
1.  MySQL メタデータ エクスプ ローラーで、次のように選択します。**スキーマ**です。  
  
    **スキーマ マッピング** タブは、個別のスキーマを選択したときにも使用可能な。 一覧で、**スキーマ マッピング** タブを選択したオブジェクトのカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブです。  
  
    対象の値が続くすべての MySQL スキーマの一覧が表示されます。 このターゲットは、2 部構成の表記法で表されます (*database.schema*) で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のオブジェクトとデータを移行します。  
  
3.  選択を行い、をクリックするマッピングを含む行**変更**です。  
  
    **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能な対象データベースとスキーマ、または型データベースおよびスキーマで 2 部構成の表記 (database.schema) で、テキスト ボックスの名前をクリックを参照することがあります**OK**です。  
  
4.  は、ターゲットの変更、**スキーマ マッピング**タブです。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベースです。 マップされているターゲット データベースが存在しないで[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージを使用するように求められますが、 **"データベースまたはスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。か続行しますか?"** [はい] をクリックします。 同様に、[ターゲット] で、存在しないスキーマをスキーマをマップできる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
-   SQL Azure へのマッピング  
  
ソース データベースをマップするには接続されているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースか、いずれのスキーマに接続されているターゲットの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 ソース スキーマ 接続されているターゲット データベースの任意の存在しないスキーマをマップするかどうかは、メッセージが求められます **"スキーマが対象のメタデータには存在できません。これが同期中に作成されます。続行しますか?"** はい をクリックします。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマを元に戻す  
MySQL スキーマと SQL Server スキーマ間のマッピングをカスタマイズする場合は、既定値に戻すマッピングを戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  スキーマのマッピング] タブで、[任意の行を選択し、をクリックして**既定値にリセット**既定のデータベースとスキーマを元に戻す。  
  
## <a name="next-steps"></a>次の手順  
MySQL オブジェクトの SQL Server または SQL Azure のオブジェクトへの変換を分析する場合は、[変換レポートを作成する](http://msdn.microsoft.com/en-us/2a56a003-3b0f-453a-963c-00c9e40933ec)できますそれ以外の場合[MySQL のデータベース オブジェクトの定義の変換](http://msdn.microsoft.com/en-us/ac21850b-fb32-4704-9985-5759b7c688c7)を SQL Server または SQL Azure のスキーマに  
  
## <a name="see-also"></a>参照  
[プロジェクト設定&#40;変換&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Azure SQL DB に接続する&#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[SQL Server - Azure SQL DB にデータベースを移行する MySQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[SQL Server に接続する&#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
