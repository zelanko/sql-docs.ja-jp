---
title: マッピングのソースとターゲット データベース (AccessToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-access
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
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ade8c301a8cb519c22413a4db9a236f58f5dd870
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>ソースとターゲット データベース (AccessToSQL) とのマッピング
接続すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 移行のターゲット データベースを指定する必要があります。 複数データベースにアクセスした場合に割り当てることに複数[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース (またはスキーマ) または接続されている SQL Azure データベースの下にある複数のスキーマにします。  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server または SQL Azure データベースのスキーマ  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースでは、スキーマの概念を使用して、データベース内のオブジェクトを論理グループに分けます。 たとえば、ライブラリ データベースでという 3 つのスキーマを使用して**ブック**、**オーディオ**、および**ビデオ**book、オーディオ、およびビデオのオブジェクトを互いから分離します。 既定では、access データベースがマップされている**マスター**データベースおよび**dbo**内のスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]と接続されているデータベースと**dbo** SQL Azure でのスキーマです。  
  
各アクセス データベースの間のマッピングをカスタマイズしない限り、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマを SSMA は、すべてのスキーマとマップされている既定のデータベースに access データベースに関連付けられているデータが移行されます。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA では、各 Access データベースをマップできます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]や SQL Azure データベース、スキーマです。 次の手順では、データベースごとのマッピングをカスタマイズする方法について説明します。  
  
**ターゲット データベースおよびスキーマを変更するには**  
  
1.  アクセス メタデータ エクスプ ローラー ペインで選択**アクセス メタデータ**です。  
  
    スキーマのマッピングは、選択した場合にも使用可能な**データベース**ノードまたはデータベースの任意のノードです。 スキーマのマッピングの一覧は、選択したオブジェクトのカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブです。  
  
    アクセスを含むテーブルを参照して、データベース名とその対応する ssNoVersion または Sql Azure のスキーマです。 ターゲット スキーマは、2 部構成の表記 (database.schema) で表されます。  
  
3.  カスタマイズ、およびをクリックするマッピングを含む行を選択して**変更**です。  
  
4.  **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能な対象データベースとスキーマ、または型データベースおよびスキーマで 2 部構成の表記 (database.schema) で、テキスト ボックスの名前をクリックを参照することがあります**OK**です。  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベースです。 マップされているターゲット データベースが存在しないかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージを使用するように求められますが、 **"データベースまたはスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。か続行しますか?"** [はい] をクリックします。 同様に、[ターゲット] で、存在しないスキーマをスキーマをマップできる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
-   SQL Azure へのマッピング  
  
ソース データベースをマップするには接続されているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースか、いずれのスキーマに接続されているターゲットの[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 ソース スキーマ 接続されているターゲット データベースの任意の存在しないスキーマをマップするかどうかは、メッセージが求められます **"スキーマが対象のメタデータには存在できません。これが同期中に作成されます。続行しますか?"** はい をクリックします。  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>最初のデータベースとスキーマを元に戻す  
Access データベースの間のマッピングをカスタマイズする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]や SQL Azure データベース、スキーマに接続するときに指定したデータベースにマッピングを戻すことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
**既定のデータベースとスキーマにリセットするには**  
  
1.  スキーマのマッピング] タブで、[任意の行を選択し、をクリックして**既定値にリセット**既定のデータベースとスキーマを元に戻す。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[データベース オブジェクトを変換します。](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
