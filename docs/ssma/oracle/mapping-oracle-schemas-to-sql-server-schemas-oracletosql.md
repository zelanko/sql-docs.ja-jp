---
title: SQL Server スキーマ (OracleToSQL) への Oracle スキーマのマッピング |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 76e532a39a7571bf90ab2b032b86ba4c5e07da44
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981304"
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>SQL Server スキーマ (OracleToSQL) への Oracle スキーマのマッピング
Oracle は、各データベースは、1 つまたは複数のスキーマを持っています。 SSMA は既定では、Oracle スキーマのすべてのオブジェクトを移行、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマという名前のデータベース。 ただし、Oracle スキーマ間のマッピングをカスタマイズすることができますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle および SQL Server スキーマ  
Oracle データベースには、スキーマが含まれています。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]複数のスキーマがそれぞれの複数のデータベースが含まれています。  
  
マップ、スキーマの Oracle の概念、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースとそのスキーマのいずれかの概念です。 たとえば、Oracle のという名前のスキーマがある**HR**します。 インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]という名前のデータベースがあります。 **HR**、そのデータベースは、スキーマとします。 1 つのスキーマは、 **dbo** (またはデータベース所有者) スキーマ。 既定では、Oracle スキーマ**HR**にマップされます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマ**HR.dbo**します。 SSMA を指す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマとしてデータベースとスキーマの組み合わせ。  
  
Oracle の間のマッピングを変更して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマ。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA では、使用可能な任意に、Oracle スキーマをマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマ。  
  
**データベースとスキーマを変更するには**  
  
1.  Oracle メタデータ エクスプ ローラーで選択**スキーマ**します。  
  
    **スキーマ マッピング** タブは、個々 のデータベースを選択した場合にも使用可能な**スキーマ**フォルダー、または個別のスキーマ。 一覧で、**スキーマ マッピング** タブを選択したオブジェクトのカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブ。  
  
    対象の値を後に、すべての Oracle スキーマの一覧が表示されます。 このターゲットは、2 部構成の表記法で示されます (*database.schema*) で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクトとデータを移行します。  
  
3.  変更、およびクリックするマッピングが含まれている行を選択**変更**します。  
  
    **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能なターゲット データベース スキーマや型、データベースとスキーマの 2 部構成の表記 (database.schema) で、テキスト ボックスに名前をクリックを参照することがあります**OK**.  
  
4.  ターゲットの変更、**スキーマ マッピング**タブ。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベース。 マップされるターゲット データベースでは、非既存ではかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージが表示されますが、 **"、データベースやスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。続行することでしょうか。"** [はい] をクリックします。 同様に、ターゲットの存在しないスキーマをスキーマにマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
## <a name="reverting-to-the-default-database-and-schema"></a>既定のデータベースとスキーマを元に戻す  
Oracle スキーマ間のマッピングをカスタマイズする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマでは、既定値にマッピングを戻すことができます。  
  
**既定のデータベースとスキーマに戻すには**  
  
1.  スキーマ マッピング タブで、任意の行を選択し をクリックして**既定値にリセット**既定のデータベースとスキーマに戻す。  
  
## <a name="next-steps"></a>次の手順  
Oracle オブジェクトの変換を分析する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクトを実行できます[変換レポートを作成する](http://msdn.microsoft.com/4de9bcf6-1346-4740-87f9-7f24a8226357)します。 それ以外の場合できます[Oracle データベースのオブジェクトの定義の変換](http://msdn.microsoft.com/e021182d-31da-443d-b110-937f5db27272)に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オブジェクト定義。  
  
## <a name="see-also"></a>参照  
[SQL Server に接続する&#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
