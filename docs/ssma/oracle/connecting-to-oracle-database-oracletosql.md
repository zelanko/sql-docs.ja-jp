---
title: Oracle Database に接続しています (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Refreshing Oracle Metadata
ms.assetid: e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: fc25c36a0d0133975414f4c7270da2974b552f40
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68266186"
---
# <a name="connecting-to-oracle-database-oracletosql"></a>Oracle データベースへの接続 (OracleToSQL)
Oracle データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するには、移行する oracle データベースに接続する必要があります。 接続すると、SSMA はすべての Oracle スキーマに関するメタデータを取得し、[Oracle メタデータエクスプローラー] ペインに表示します。 SSMA は、データベースサーバーに関する情報を格納しますが、パスワードは保存しません。  
  
データベースへの接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、データベースへのアクティブな接続が必要な場合は、再接続する必要があります。  
  
Oracle データベースに関するメタデータは自動的に更新されません。 代わりに、Oracle メタデータエクスプローラーでメタデータを更新する場合は、手動で更新する必要があります。 詳細については、このトピックで後述する「Oracle メタデータの更新」セクションを参照してください。  
  
## <a name="required-oracle-permissions"></a>必要な Oracle 権限  
Oracle データベースへの接続に使用するアカウントには、少なくとも**接続**権限が必要です。 これにより、SSMA は、接続しているユーザーが所有するスキーマからメタデータを取得できるようになります。 他のスキーマのオブジェクトのメタデータを取得し、そのスキーマ内のオブジェクトを変換するには、アカウントに次の権限が必要です。  
  
-   任意のプロシージャを作成する  
  
-   任意のプロシージャを実行する  
  
-   任意のテーブルを選択します  
  
-   任意のシーケンスを選択します  
  
-   任意の型を作成する  
  
-   任意のトリガーを作成する  
  
-   任意の辞書を選択します  
  
## <a name="establishing-a-connection-to-oracle"></a>Oracle への接続の確立  
データベースに接続すると、SSMA によってデータベースのメタデータが読み取られ、このメタデータがプロジェクトファイルに追加されます。 このメタデータは、SSMA がオブジェクトを構文に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変換するとき、およびにデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行するときに使用されます。 このメタデータは、[Oracle メタデータエクスプローラー] ペインで参照して、個々のデータベースオブジェクトのプロパティを確認できます。  
  
> [!IMPORTANT]  
> 接続を試行する前に、データベースサーバーが実行されていて、接続を受け入れることができることを確認してください。  
  
**Oracle に接続するには**  
  
1.  [**ファイル**] メニューの [ **Oracle への接続**] をクリックします。  
  
    以前に Oracle に接続していた場合は、コマンド名が**oracle に再接続**されます。  
  
2.  [**プロバイダー** ] ボックスで、インストールされているプロバイダーに応じて [ **Oracle クライアントプロバイダー** ] または [ **OLE DB プロバイダー**] を選択します。 既定値は [Oracle client (Oracle クライアント) です。  
  
3.  [**モード**] ボックスで、[**標準モード**]、[ **tnsname モード**]、または [**接続文字列モード**] を選択します。  
  
    サーバー名とポートを指定するには、標準モードを使用します。 サービス名モードを使用して、Oracle サービス名を手動で指定します。 接続文字列モードを使用して、完全な接続文字列を指定します。  
  
4.  [標準]**モード**を選択した場合は、次の値を指定します。  
  
    1.  [**サーバー名**] ボックスで、データベースサーバーの名前または IP アドレスを入力または選択します。  
  
    2.  データベースサーバーが既定のポート (1521) で接続を受け入れるように構成されていない場合は、[**サーバーポート**] ボックスに、Oracle 接続に使用するポート番号を入力します。  
  
    3.  [ **ORACLE SID** ] ボックスに、システム識別子を入力します。  
  
    4.  [**ユーザー名**] ボックスに、必要なアクセス許可を持つ Oracle アカウントを入力します。  
  
    5.  [**パスワード**] ボックスに、指定したユーザー名のパスワードを入力します。  
  
5.  **Tnsname モード**を選択した場合は、次の値を指定します。  
  
    1.  [**接続識別子**] ボックスに、データベースの接続識別子 (TNS alias) を入力します。  
  
    2.  [**ユーザー名**] ボックスに、必要なアクセス許可を持つ Oracle アカウントを入力します。  
  
    3.  [**パスワード**] ボックスに、指定したユーザー名のパスワードを入力します。  
  
6.  **接続文字列モード**を選択した場合は、[**接続文字列**] ボックスに接続文字列を指定します。  
  
    次の例は、OLE DB 接続文字列を示しています。  
  
    `Provider=OraOLEDB.Oracle;Data Source=MyOracleDB;User Id=myUsername;Password=myPassword;`  
  
    次の例は、統合セキュリティを使用する Oracle クライアント接続文字列を示しています。  
  
    `Data Source=MyOracleDB;Integrated Security=yes;`  
  
    詳細については、「 [Connect To Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)」を参照してください。  
  
## <a name="reconnecting-to-oracle"></a>Oracle への再接続  
データベースサーバーへの接続は、プロジェクトを閉じるまでアクティブなままになります。 プロジェクトを再度開いたときに、データベースへのアクティブな接続が必要な場合は、再接続する必要があります。 メタデータを更新したり、データベースオブジェクトをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込んだり、データを移行したりするまで、オフラインで作業することができます。  
  
## <a name="refreshing-oracle-metadata"></a>Oracle メタデータの更新  
Oracle データベースに関するメタデータは自動的には更新されません。 Oracle メタデータエクスプローラーのメタデータは、最初に接続したとき、またはメタデータを手動で更新したときにメタデータのスナップショットになります。 すべてのスキーマ、単一のスキーマ、または個々のデータベースオブジェクトのメタデータを手動で更新できます。  
  
**メタデータを更新するには**  
  
1.  データベースに接続していることを確認します。  
  
2.  Oracle メタデータエクスプローラーで、更新する各スキーマまたはデータベースオブジェクトの横にあるチェックボックスをオンにします。  
  
3.  [**スキーマ**]、または個々のスキーマまたはデータベースオブジェクトを右クリックし、[**データベースから更新**] を選択します。  
  
    アクティブな接続がない場合は、SSMA によって [ **Oracle への接続**] ダイアログボックスが表示され、接続できるようになります。  
  
4.  [データベースから更新] ダイアログボックスで、更新するオブジェクトを指定します。  
  
    -   オブジェクトを更新するには、オブジェクトの横にある**アクティブ**フィールドをクリックして、矢印が表示されるようにします。  
  
    -   オブジェクトが更新されないようにするには、 **X**が表示されるまで、オブジェクトの横にある**アクティブな**フィールドをクリックします。  
  
    -   オブジェクトのカテゴリを更新または拒否するには、category フォルダーの横にある**アクティブな**フィールドをクリックします。  
  
    色分けの定義を表示するには、[**凡例**] ボタンをクリックします。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-step"></a>次の手順  
  
-   移行プロセスの次の手順では、 [SQL Server のインスタンスに接続](connecting-to-sql-server-oracletosql.md)します。  
  
## <a name="see-also"></a>参照  
[Oracle データベースの SQL Server &#40;OracleToSQL&#41;への移行](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
