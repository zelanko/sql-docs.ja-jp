---
title: SQL Server スキーマ (OracleToSQL) への Oracle スキーマのマッピング |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: e375c07ceddc995b599930c14f00710af040d6c0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68262910"
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>SQL Server スキーマへの Oracle スキーマのマッピング (OracleToSQL)
Oracle では、各データベースに1つ以上のスキーマがあります。 既定では、SSMA は、Oracle スキーマ内のすべての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトを、スキーマのという名前のデータベースに移行します。 ただし、Oracle スキーマと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース間のマッピングをカスタマイズすることはできます。  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle スキーマと SQL Server スキーマ  
Oracle データベースには、スキーマが含まれています。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスには複数のデータベースが含まれており、それぞれが複数のスキーマを持つことができます。  
  
スキーマの Oracle の概念は、データベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]概念とそのスキーマの1つにマップされます。 たとえば、Oracle には**HR**という名前のスキーマが存在する場合があります。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスには、 **HR**という名前のデータベースがあり、そのデータベース内にはスキーマがあります。 1つのスキーマは、 **dbo** (またはデータベース所有者) スキーマです。 既定では、Oracle スキーマの**hr**はデータベースとスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**hr. dbo**にマップされます。 SSMA とは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマとしてのデータベースとスキーマの組み合わせを意味します。  
  
Oracle と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマ間のマッピングを変更できます。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲットデータベースとスキーマの変更  
SSMA では、Oracle スキーマを任意の使用可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマにマップできます。  
  
**データベースとスキーマを変更するには**  
  
1.  Oracle メタデータエクスプローラーで、[**スキーマ**] を選択します。  
  
    [**スキーママッピング**] タブは、個々のデータベース、**スキーマ**フォルダー、または個々のスキーマを選択した場合にも使用できます。 [**スキーママッピング**] タブの一覧は、選択したオブジェクトに合わせてカスタマイズされています。  
  
2.  右ペインで、[**スキーママッピング**] タブをクリックします。  
  
    すべての Oracle スキーマの一覧が表示され、その後にターゲット値が表示されます。 このターゲットは、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトとデータを移行する2つの部分表記 (*データベーススキーマ*) で示されています。  
  
3.  変更するマッピングを含む行を選択し、[**変更**] をクリックします。  
  
    [**ターゲットスキーマの選択**] ダイアログボックスで、使用可能なターゲットデータベースとスキーマを参照するか、2つの部分表記 (データベーススキーマ) のテキストボックスにデータベースとスキーマ名を入力し、[ **OK**] をクリックします。  
  
4.  [**スキーママッピング**] タブでターゲットが変更されます。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソースデータベースを任意のターゲットデータベースにマップできます。 既定では、ソースデータベースは SSMA を使用して接続したターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースにマップされます。 マップされているターゲットデータベースがに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存在しない場合は、 **"データベースまたはスキーマがターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータに存在しません" というメッセージが表示されます。同期中に作成されます。続行しますか? "** [はい] をクリックします。 同様に、スキーマを、同期中に作成される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットデータベース下に存在しないスキーマにマップすることもできます。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマに戻す  
Oracle スキーマと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマ間のマッピングをカスタマイズする場合は、マッピングを既定値に戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  [スキーママッピング] タブで、任意の行を選択し、[既定**値にリセット**] をクリックして既定のデータベースとスキーマに戻します。  
  
## <a name="next-steps"></a>次のステップ  
Oracle オブジェクトからオブジェクトへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の変換を分析する場合は、[変換レポートを作成](assessing-oracle-schemas-for-conversion-oracletosql.md)できます。 それ以外の場合は[、Oracle データベースオブジェクト定義](converting-oracle-schemas-oracletosql.md)をオブジェクト定義に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換できます。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;OracleToSQL&#41;に接続しています](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Oracle データベースの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
