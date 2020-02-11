---
title: Sybase ASE スキーマを SQL Server スキーマにマップする (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5c39e81f8faffed606e6ca94315c47d383174c91
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028872"
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Sybase ASE スキーマの SQL Server スキーマへのマッピング (SybaseToSQL)
Sybase Adaptive Server Enterprise (ASE) では、各データベースに1つ以上のスキーマがあります。 既定では、SSMA は、データベース内のすべてのオブジェクトとスキーマを、または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure の同じデータベースおよびスキーマに移行します。 ただし、ASE と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure データベースおよびスキーマ間のマッピングはカスタマイズできます。  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE および SQL Server または SQL Azure スキーマ  
ASE と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure は、両方ともデータベースとそのスキーマを指定します。これは、2つの部分で構成される*スキーマ*として使用します。 たとえば、ASE**デモ**データベースでは、 **dbo**スキーマが存在する可能性があります。 そのデータベースとスキーマのペアは、 **demo. dbo**として指定されます。 また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure に同じデータベースとスキーマが指定されている場合は、そのペアも**demo. dbo**として指定されます。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲットデータベースとスキーマの変更  
SSMA では、ASE スキーマを任意の使用可能[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure スキーマにマップできます。  
  
**データベースとスキーマを変更するには**  
  
1.  Sybase メタデータエクスプローラーで、[**データベース**] を選択します。  
  
    [**スキーママッピング**] タブは、個々のデータベース、**スキーマ**フォルダー、または個々のスキーマを選択した場合にも使用できます。 [**スキーママッピング**] タブの一覧は、選択したオブジェクトに合わせてカスタマイズされています。  
  
2.  右ペインで、[**スキーママッピング**] タブをクリックします。  
  
    すべての ASE データベースとそのスキーマとターゲット値の一覧が表示されます。 このターゲットは、または SQL Azure の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2 つの部分表記 (*データベーススキーマ*) で表され、オブジェクトとデータが移行されます。  
  
3.  変更するマッピングを含む行を選択し、[**変更**] をクリックします。  
  
4.  [**ターゲットスキーマの選択**] ダイアログボックスで、使用可能なターゲットデータベースとスキーマを参照するか、2つの部分表記 (データベーススキーマ) のテキストボックスにデータベースとスキーマ名を入力し、[ **OK**] をクリックします。  
  
5.  [**スキーママッピング**] タブでターゲットが変更されます。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソースデータベースを任意のターゲットデータベースにマップできます。 既定では、ソースデータベースは SSMA を使用して接続したターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースにマップされます。 マップされているターゲットデータベースがに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存在しない場合は、 **"データベースまたはスキーマがターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータに存在しません" というメッセージが表示されます。同期中に作成されます。続行しますか? "** [はい] をクリックします。 同様に、スキーマを、同期中に作成される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットデータベース下に存在しないスキーマにマップすることもできます。  
  
-   SQL Azure へのマッピング  
  
ソースデータベースは、接続されているターゲット SQL Azure データベース、または接続されているターゲット SQL Azure データベースの任意のスキーマにマップできます。 送信元スキーマを [接続されたターゲットデータベース] の既存ではないスキーマにマップすると、 **"スキーマはターゲットメタデータに存在しません" というメッセージが表示されます。同期中に作成されます。続行しますか?[はい] をクリックし**ます。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマに戻す  
ASE スキーマと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure スキーマ間のマッピングをカスタマイズする場合は、マッピングを既定値に戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  [スキーママッピング] タブで、任意の行を選択し、[既定**値にリセット**] をクリックして既定のデータベースとスキーマに戻します。  
  
## <a name="next-steps"></a>次の手順  
Sybase ASE オブジェクトからオブジェクトへの変換または SQL Azure オブジェクト[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]への変換を分析する場合は、[変換レポートを作成](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md)できます。 それ以外の場合は[、ASE データベースオブジェクト定義](converting-sybase-ase-database-objects-sybasetosql.md)をまたは SQL Azure オブジェクト定義に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換できます。  
  
## <a name="see-also"></a>参照  
[Sybase ASE データベースの SQL Server への移行-Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
