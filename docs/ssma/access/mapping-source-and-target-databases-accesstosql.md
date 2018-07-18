---
title: ソースとターゲット データベース (AccessToSQL) のマッピング |Microsoft Docs
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
ms.openlocfilehash: d0a76c4fdeff8abbe2b5e1ba2bafd615bba4b919
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38980165"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>ソースとターゲット データベース (AccessToSQL) のマッピング
接続すると[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の移行のターゲット データベースを指定する必要があります。 複数データベースにアクセスした場合も複数とそれらにマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース (またはスキーマ) または接続されている SQL Azure データベースで複数のスキーマにします。  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server または SQL Azure データベースのスキーマ  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースでは、スキーマの概念を使用して、データベース内のオブジェクトを論理グループに分割します。 たとえば、ライブラリのデータベースでという名前の 3 つのスキーマを使用して**ブックの「**、**オーディオ**、および**ビデオ**から他の書籍オーディオ、およびビデオのオブジェクトを分離しますします。 既定では、access データベースにマップされて**マスター**データベースと**dbo**でスキーマ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続されているデータベースと**dbo** SQL Azure でのスキーマ。  
  
各アクセス データベースの間のマッピングをカスタマイズしない限り、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースおよびスキーマを SSMA は、すべてのスキーマとマップされている既定のデータベースに access データベースに関連付けられているデータが移行されます。  
  
## <a name="modifying-the-target-database-and-schema"></a>ターゲット データベースおよびスキーマの変更  
SSMA では、各 Access データベースをマップできます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]や SQL Azure データベース、スキーマ。 次の手順では、データベースごとのマッピングをカスタマイズする方法について説明します。  
  
**ターゲット データベースとスキーマを変更するには**  
  
1.  アクセス メタデータ エクスプ ローラー ウィンドウで選択**アクセス メタデータ**します。  
  
    スキーマのマッピングは、選択した場合にも使用可能な**データベース**ノードまたはデータベースの任意のノード。 スキーマ マッピングの一覧は、選択したオブジェクトをカスタマイズします。  
  
2.  右側のウィンドウでをクリックして、**スキーマ マッピング**タブ。  
  
    アクセスを含むテーブルを参照してください、データベース名および対応する ssNoVersion や Sql Azure のスキーマ。 ターゲット スキーマは、2 部構成の表記 (database.schema) で示されます。  
  
3.  クリックして、カスタマイズするマッピングが含まれている行を選択**変更**します。  
  
4.  **ターゲット スキーマの選択**ダイアログ ボックスで、使用可能なターゲット データベース スキーマや型、データベースとスキーマの 2 部構成の表記 (database.schema) で、テキスト ボックスに名前をクリックを参照することがあります**OK**.  
  
**マッピングのモード**  
  
-   SQL Server へのマッピング  
  
ソース データベースは、任意のターゲット データベースにマップできます。 既定では、ソース データベースがマップされているターゲットに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA を使用してを接続したデータベース。 マップされるターゲット データベースが存在しないかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、メッセージが表示されますが、 **"、データベースやスキーマがターゲットに存在しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。これが同期中に作成されます。続行することでしょうか。"** [はい] をクリックします。 同様に、ターゲットの存在しないスキーマをスキーマにマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]同期中に作成されるデータベース。  
  
-   SQL Azure へのマッピング  
  
接続されているターゲットをソース データベースにマップできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースまたは接続されているターゲットのスキーマに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 ソース スキーマ 接続されているターゲット データベースでは、存在しないスキーマをマップするかどうかは、メッセージが表示されるが **"スキーマが対象のメタデータには存在できません。これが同期中に作成されます。続行しますか?"** はい をクリックします。  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>初期データベースとスキーマを元に戻す  
Access データベースの間のマッピングをカスタマイズする場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]や SQL Azure データベース、スキーマ、データベースに接続するときに指定したマッピングを戻すことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
**既定のデータベースとスキーマをリセットするには**  
  
1.  スキーマ マッピング タブで、任意の行を選択し をクリックして**既定値にリセット**既定のデータベースとスキーマに戻す。  
  
## <a name="next-step"></a>次の手順  
移行プロセスでは、次の手順は[データベース オブジェクトの変換](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
