---
title: ソースデータベースとターゲットデータベースのマッピング (Sql server の場合) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 192db2e6c074305ca258d76652351175c8a82751
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907156"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>ソースデータベースとターゲットデータベースのマッピング (Sql server)
または SQL Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続する場合は、移行するターゲットデータベースを指定する必要があります。 複数の Access データベースがある場合は、複数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータベース (またはスキーマ)、または接続されている SQL Azure データベースの複数のスキーマにマップできます。  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server または SQL Azure データベーススキーマ  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースでは、スキーマの概念を使用して、データベース内のオブジェクトを論理グループに分割します。 たとえば、ライブラリデータベースでは、 **books**、 **audio**、video という3つのスキーマを使用して、書籍、オーディオ、およびビデオオブジェクトを相互に**分離すること**ができます。 既定では、access データベースは、の**master**データベースおよび**dbo**スキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に、SQL Azure の接続されたデータベースおよび**dbo**スキーマにマップされます。  
  
各 Access データベースと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースおよびスキーマ間のマッピングをカスタマイズしない限り、ssma は、access データベースに関連付けられているすべてのスキーマとデータを、マップされた既定のデータベースに移行します。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲットデータベースとスキーマの変更  
SSMA を使用すると、各 Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースをまたは SQL Azure データベースおよびスキーマにマップできます。 次の手順では、データベースごとにマッピングをカスタマイズする方法について説明します。  
  
**ターゲットデータベースとスキーマを変更するには**  
  
1.  [メタデータエクスプローラーにアクセス] ウィンドウで、[**アクセス-メタデータ**] を選択します。  
  
    スキーママッピングは、[**データベース**] ノードまたは任意のデータベースノードを選択した場合にも使用できます。 [スキーママッピング] の一覧は、選択したオブジェクトに合わせてカスタマイズされています。  
  
2.  右ペインで、[**スキーママッピング**] タブをクリックします。  
  
    Access データベース名とそれに対応する ssNoVersion または Sql Azure スキーマを含むテーブルが表示されます。 ターゲットスキーマは、2つの部分表記 (データベーススキーマ) で示されます。  
  
3.  カスタマイズするマッピングが含まれている行を選択し、[**変更**] をクリックします。  
  
4.  [**ターゲットスキーマの選択**] ダイアログボックスで、使用可能なターゲットデータベースとスキーマを参照するか、2つの部分表記 (データベーススキーマ) のテキストボックスにデータベースとスキーマ名を入力し、[ **OK**] をクリックします。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソースデータベースを任意のターゲットデータベースにマップできます。 既定では、ソースデータベースは SSMA を使用して接続したターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースにマップされます。 マップされているターゲットデータベースがに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]存在しない場合は、 **"データベースまたはスキーマがターゲット[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メタデータに存在しません" というメッセージが表示されます。同期中に作成されます。続行しますか? "** [はい] をクリックします。 同様に、スキーマを、同期中に作成される[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ターゲットデータベース下に存在しないスキーマにマップすることもできます。  
  
-   SQL Azure へのマッピング  
  
接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]先データベースまたは接続先[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースの任意のスキーマに、ソースデータベースをマップできます。 送信元スキーマを [接続されたターゲットデータベース] の既存ではないスキーマにマップすると、 **"スキーマはターゲットメタデータに存在しません" というメッセージが表示されます。同期中に作成されます。続行しますか?[はい] をクリックし**ます。  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>最初のデータベースとスキーマに戻す  
Access データベースと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure データベースとスキーマ間のマッピングをカスタマイズする場合は、に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続したとき、または SQL Azure したときに指定したデータベースにマッピングを戻すことができます。  
  
**既定のデータベースとスキーマにリセットするには**  
  
1.  [スキーママッピング] タブで、任意の行を選択し、[既定**値にリセット**] をクリックして既定のデータベースとスキーマに戻します。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順では、[データベースオブジェクトを変換](converting-access-database-objects-accesstosql.md)します。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
