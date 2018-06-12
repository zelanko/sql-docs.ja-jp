---
title: データベース オブジェクト (AccessToSQL) に変換する |Microsoft ドキュメント
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
- Access databases
- Access databases, converting schemas
- conversion
- conversion, converting schemas
- indexes, altering
- metadata
- metadata, altering
- metadata, converting
- migrating databases, one-click
- one-click migration
- schemas
- schemas, converting
- SQL
- SQL, converting
- syntax
- syntax, converting
- tables, altering
- translating Access to SQL Azure
- translating Access to SQL Server
ms.assetid: e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 36d73e04296346bd0c44a8459ec157d437df8583
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773478"
---
# <a name="converting-access-database-objects-accesstosql"></a>データベース オブジェクト (AccessToSQL) に変換します。
Access データベースを追加してに接続した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、SSMA は、アクセスするためのメタデータを表示および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベースのオブジェクト。 今すぐアクセス データベースのオブジェクトを選択してへのスキーマを変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のスキーマです。  
  
## <a name="the-conversion-process"></a>変換プロセス  
アクセス メタデータからオブジェクト定義を受け取り、それと同等に変換してデータベース オブジェクトを変換する[!INCLUDE[tsql](../../includes/tsql_md.md)]構文、およびプロジェクトにこの情報を読み込みます。 表示することができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトとそのプロパティを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラー。  
  
> [!IMPORTANT]  
> オブジェクトの変換でオブジェクトを作成しません[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 のみ、オブジェクトの定義に変換し、SSMA プロジェクトで情報を格納します。  
  
変換中は、SSMA は、出力 ウィンドウで、エラー、警告、およびエラー一覧 ウィンドウに情報メッセージをステータスを出力します。 この情報を使用して、Access データベースまたは必要な変換の結果を得るため、変換プロセスを変更する必要があるかどうかを判断します。 内の情報を使用することも、 [Access データベースを移行の準備](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)は新機能と、変換されませんを判断するトピックです。  
  
## <a name="setting-conversion-options"></a>変換オプションの設定  
オブジェクトを変換する前に、プロジェクトの変換オプションを確認、**プロジェクト設定** ダイアログ ボックス。 このダイアログ ボックスを使用すると、SSMA がインデックス付きのメモ列、主キー、外部キー制約、タイムスタンプ、およびインデックスなしテーブルに変換する方法を設定することができます。 詳細については、次を参照してください[プロジェクトの設定 (変換)。](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388)  
  
## <a name="conversion-results"></a>変換結果  
次の表は、変換されますが、オブジェクトのアクセスと、結果として得られる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクト。  
  
|オブジェクトにアクセス|結果の SQL Server オブジェクト|  
|-----------------|-------------------------------|  
|テーブル|テーブル|  
|column|column|  
|インデックス (index)|インデックス (index)|  
|外部キー (foreign key)|外部キー (foreign key)|  
|query|view<br /><br />ほとんどの SELECT クエリは、ビューをビューに変換されます。 更新クエリなど、他のクエリは移行されません。<br /><br />パラメーターを受け取る SELECT クエリは変換されません。 またクロス集計クエリ。|  
|レポート|変換されませんでした。|  
|フォーム|変換されませんでした。|  
|マクロ|変換されませんでした。|  
|モジュール (module)|変換されませんでした。|  
|既定値|既定値|  
|0 個の長列のプロパティを許可します。|check 制約|  
|列の検証規則|check 制約|  
|テーブルの検証規則|check 制約|  
|主キー (primary key)|主キー (primary key)|  
  
## <a name="converting-access-objects"></a>オブジェクトへのアクセスを変換します。  
データベース オブジェクトを変換するには、最初に変換し、変換を行う SSMA オブジェクトを選択する必要があります。 変換中に出力メッセージを表示する、**ビュー**メニューの **出力**です。  
  
**選択し、データベース オブジェクトへのアクセスを SQL Server または SQL Azure の構文に変換します。**  
  
1.  メタデータ エクスプ ローラーでのアクセス、**アクセス メタベース**、順に展開**データベース**です。  
  
2.  次の 1 つ以上の操作を行います。  
  
    -   すべてのデータベースを変換するには、チェック ボックスを横に選択**データベース**です。  
  
    -   変換するか、個々 のデータベースを省略、オンまたはデータベース名の横にあるチェック ボックスをオフにします。  
  
    -   変換またはクエリの省略は、データベースを展開しをオンまたはオフ、**クエリ**チェック ボックスをオンします。  
  
    -   変換または個々 のテーブルの省略は、データベースを展開し、**テーブル**を選択するか、テーブルの横にあるチェック ボックスをオフにします。  
  
3.  次のいずれかの操作を行います。  
  
    -   スキーマを変換するを右クリックして**データベース**選択**スキーマの変換**です。  
  
        個々 のオブジェクトを変換することもできます。 オブジェクトの選択に関係なく、オブジェクトに変換するオブジェクトを右クリックし **変換スキーマ**です。  
  
        オブジェクトが変換されると、太字アクセス メタデータ エクスプ ローラーに表示されます。  
  
    -   変換、読み込み、し、スキーマと 1 つの手順でデータを移行するには、データベースと選択 を右クリックし**変換、読み込み、および移行**です。  
  
4.  表示されるメッセージで、**出力**ペインと、エラーや警告の**エラー一覧**ウィンドウです。  
  
## <a name="altering-tables-and-indexes"></a>テーブルとパーティション インデックスを変更します。  
メタデータにアクセスするを変換した後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータにオブジェクトを読み込む前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure を変更したりできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure のテーブルとパーティション インデックス。  
  
**テーブルまたはインデックスのプロパティを変更するには**  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure メタデータ エクスプ ローラーで、テーブルまたはインデックスを変更するを選択します。  
  
2.  **テーブル** タブで、変更をし、入力するか、新しい設定を選択するプロパティをクリックします。 たとえば、nvarchar (20)、nvarchar (15) に変更したり、テーブル列を null 許容にする チェック ボックスをオンにします。  
  
    変更されたプロパティのセル外、カーソルを移動します。 別の行をクリックするか、Tab キーを押すと、これを行うことができます。  
  
3.  **[適用]** をクリックします。  
  
コードの変更を表示できます、 **SQL**タブです。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順は[変換後のデータベース オブジェクトを SQL Server に読み込む](http://msdn.microsoft.com/en-us/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba)  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
