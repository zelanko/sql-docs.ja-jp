---
title: DB2 スキーマを SQL Server スキーマ (DB2ToSQL) にマッピングするMicrosoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 50845a9bdf3c3185d7b69bb86a75b2a3d332ef6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074174"
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>DB2 スキーマを SQL Server スキーマ (DB2ToSQL) にマッピングする
DB2 では、各データベースに1つ以上のスキーマがあります。 既定では、SSMA は、DB2 スキーマ内のすべての[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトを、スキーマのという名前のデータベースに移行します。 ただし、DB2 スキーマと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース間のマッピングをカスタマイズすることはできます。  
  
## <a name="db2-and-sql-server-schemas"></a>DB2 および SQL Server スキーマ  
DB2 データベースにはスキーマが含まれています。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスには複数のデータベースが含まれており、それぞれが複数のスキーマを持つことができます。  
  
DB2 のスキーマの概念は、データベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]概念とそのスキーマの1つにマップされます。 たとえば、DB2 に**HR**という名前のスキーマがあるとします。 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスには、 **HR**という名前のデータベースがあり、そのデータベース内にはスキーマがあります。 1つのスキーマは、 **dbo** (またはデータベース所有者) スキーマです。 既定では、DB2 スキーマの**hr**はデータベースとスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**hr. dbo**にマップされます。 SSMA とは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマとしてのデータベースとスキーマの組み合わせを意味します。  
  
DB2 と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマ間のマッピングを変更できます。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲットデータベースとスキーマの変更  
SSMA では、使用可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]任意のスキーマに DB2 スキーマをマップできます。  
  
**データベースとスキーマを変更するには**  
  
1.  DB2 メタデータエクスプローラーで、[**スキーマ**] を選択します。  
  
    [**スキーママッピング**] タブは、個々のデータベース、**スキーマ**フォルダー、または個々のスキーマを選択した場合にも使用できます。 [**スキーママッピング**] タブの一覧は、選択したオブジェクトに合わせてカスタマイズされています。  
  
2.  右ペインで、[**スキーママッピング**] タブをクリックします。  
  
    すべての DB2 スキーマの一覧が表示され、その後にターゲット値が表示されます。 このターゲットは、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトとデータを移行する2つの部分表記 (*データベーススキーマ*) で示されています。  
  
3.  変更するマッピングを含む行を選択し、[**変更**] をクリックします。  
  
    [**ターゲットスキーマの選択**] ダイアログボックスで、使用可能なターゲットデータベースとスキーマを参照するか、2つの部分表記 (データベーススキーマ) のテキストボックスにデータベースとスキーマ名を入力し、[ **OK**] をクリックします。  
  
4.  [**スキーママッピング**] タブでターゲットが変更されます。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソースデータベースを任意のターゲットデータベースにマップできます。 既定では、ソースデータベースは SSMA を使用して接続したターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースにマップされます。 マップされているターゲットデータベースがに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存在しない場合は、 **"データベースまたはスキーマがターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータに存在しません" というメッセージが表示されます。同期中に作成されます。続行しますか? "** [はい] をクリックします。 同様に、スキーマを、同期中に作成される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットデータベース下に存在しないスキーマにマップすることもできます。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマに戻す  
DB2 スキーマと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]スキーマ間のマッピングをカスタマイズする場合は、マッピングを既定値に戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  [スキーママッピング] タブで、任意の行を選択し、[既定**値にリセット**] をクリックして既定のデータベースとスキーマに戻します。  
  
## <a name="next-steps"></a>次の手順  
DB2 オブジェクトからオブジェクトへ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の変換を分析する場合は、[データ移行レポート (ssma Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)を使用できます。  
  
## <a name="see-also"></a>参照  
[SQL Server &#40;DB2eToSQL&#41;に接続しています](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[DB2 データベースを SQL Server &#40;DB2ToSQL&#41;に移行する](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
