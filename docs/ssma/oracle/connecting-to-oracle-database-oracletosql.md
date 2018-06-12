---
title: Oracle データベース (OracleToSQL) への接続 |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Refreshing Oracle Metadata
ms.assetid: e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2ac66c6e09706242434225b2d399320224bb0d88
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34777148"
---
# <a name="connecting-to-oracle-database-oracletosql"></a>Oracle データベース (OracleToSQL) に接続します。
Oracle データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、移行する Oracle データベースに接続する必要があります。 接続すると、SSMA は、すべての Oracle スキーマに関するメタデータを取得し、Oracle メタデータ エクスプ ローラー ペインに表示します。 SSMA は、データベース サーバーに関する情報を格納しますが、パスワードは保存されません。  
  
プロジェクトを終了するまで、データベースへの接続をアクティブに保ちます。 プロジェクトを再度開くと、データベースにアクティブに接続する場合を再接続する必要があります。  
  
Oracle データベースについてのメタデータは自動的に更新されません。 代わりに、Oracle メタデータ エクスプ ローラー内のメタデータを更新する場合は、手動で更新してください。 詳細については、このトピックの「「Oracle メタデータを更新する」セクションを参照してください。  
  
## <a name="required-oracle-permissions"></a>必要な Oracle の権限  
Oracle データベースへの接続に使用されるアカウントが少なくとも必要**接続**アクセス許可。 これにより、SSMA を接続しているユーザーが所有するスキーマからメタデータを取得します。 他のスキーマ内のオブジェクトのメタデータを取得し、それらのスキーマ内のオブジェクトを変換は、次のアクセス許可がアカウントに必要です。  
  
-   すべてのプロシージャを作成します。  
  
-   すべてのプロシージャを実行します。  
  
-   任意のテーブルを選択します。  
  
-   任意の順序を選択します  
  
-   任意の型を作成します。  
  
-   いずれかのトリガーを作成します。  
  
-   辞書を選択します。  
  
## <a name="establishing-a-connection-to-oracle"></a>Oracle への接続を確立します。  
データベースに接続して SSMA データベースのメタデータを読み取り、プロジェクト ファイルにこのメタデータが追加されます。 このメタデータは、オブジェクトに変換するとき、SSMA によって使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構文へのデータを移行したときと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 Oracle メタデータ エクスプ ローラー ウィンドウでこのメタデータを参照して、個々 のデータベース オブジェクトのプロパティを確認できます。  
  
> [!IMPORTANT]  
> 接続は、ことを確認しようとする前に、データベース サーバーが実行されていると、接続を受け入れることができます。  
  
**Oracle に接続するには**  
  
1.  **ファイル**メニューの  **Connect to Oracle**です。  
  
    コマンド名にするは Oracle に接続されていた場合**Oracle への再接続**です。  
  
2.  **プロバイダー**ボックスで、 **Oracle クライアント プロバイダー**または**OLE DB プロバイダー**にプロバイダーがインストールされている依存します。 既定値は、Oracle クライアントです。  
  
3.  **モード**ボックスで、いずれかを選択**標準モード**、 **TNSNAME モード**、または**接続文字列モード**です。  
  
    標準モードを使用すると、サーバー名とポートを指定できます。 Oracle のサービス名を手動で指定するのにには、サービス名のモードを使用します。 接続文字列のモードを使用すると、完全な接続文字列を提供します。  
  
4.  選択した場合**標準モード**の値を指定します。  
  
    1.  **サーバー名**ボックスで、入力するか、またはデータベース サーバーの IP アドレスを選択します。  
  
    2.  既定値 (1521) のポートでは、Oracle 接続で使用されるポート番号を入力に接続を受け入れるように、データベース サーバーが構成されていない場合、**サーバー ポート**ボックス。  
  
    3.  **Oracle SID**ボックスに、システム識別子を入力します。  
  
    4.  **ユーザー名**ボックスで、必要なアクセス許可を持つ Oracle アカウントを入力します。  
  
    5.  **パスワード**ボックスで、指定されたユーザー名のパスワードを入力します。  
  
5.  選択した場合**TNSNAME モード**、次の値を指定します。  
  
    1.  **接続識別子**入力ボックスに、データベースの識別子 (TNS 別名) を接続します。  
  
    2.  **ユーザー名**ボックスで、必要なアクセス許可を持つ Oracle アカウントを入力します。  
  
    3.  **パスワード**ボックスで、指定されたユーザー名のパスワードを入力します。  
  
6.  選択した場合**接続文字列モード**での接続文字列を指定、**接続文字列**ボックス。  
  
    次の例は、OLE DB 接続文字列を示しています。  
  
    `Provider=OraOLEDB.Oracle;Data Source=MyOracleDB;User Id=myUsername;Password=myPassword;`  
  
    次の例は、統合セキュリティを使用する Oracle クライアント接続文字列を示しています。  
  
    `Data Source=MyOracleDB;Integrated Security=yes;`  
  
    詳細については、次を参照してください。 [Oracle に接続&#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)です。  
  
## <a name="reconnecting-to-oracle"></a>Oracle への再接続  
プロジェクトを終了するまで、データベース サーバーへの接続をアクティブに保ちます。 プロジェクトを再度開くと、データベースにアクティブに接続する場合を再接続する必要があります。 メタデータを更新するには、データベース オブジェクトに読み込む必要がなくなるまでオフラインで作業できる[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データを移行します。  
  
## <a name="refreshing-oracle-metadata"></a>Oracle のメタデータの更新  
Oracle データベースについてのメタデータは、自動的に更新されません。 Oracle メタデータ エクスプ ローラー内のメタデータは、最初に接続したときのメタデータまたはメタデータを手動で更新された前回のスナップショットです。 すべてのスキーマ、1 つのスキーマ、または個々 のデータベース オブジェクトのメタデータを手動で更新することができます。  
  
**メタデータを更新するには**  
  
1.  データベースに接続していることを確認します。  
  
2.  Oracle メタデータ エクスプ ローラーで、更新する各スキーマまたはデータベース オブジェクトの横にあるチェック ボックスを選択します。  
  
3.  右クリック**スキーマ**、または個々 のスキーマまたはデータベース オブジェクトをクリックし **データベースから更新**です。  
  
    SSMA が表示されます、アクティブな接続があるない場合、 **Oracle への接続** ダイアログ ボックスの接続できるようにします。  
  
4.  [データベース] ダイアログ ボックスから、更新では、更新するには、どのオブジェクトを指定します。  
  
    -   オブジェクトを更新するには、クリックして、 **Active**矢印が表示されるまで、オブジェクトの横にあるフィールドです。  
  
    -   オブジェクトが更新されていることを防ぐためにクリックして、 **Active**までオブジェクトの横にあるフィールド、 **X**が表示されます。  
  
    -   更新か、オブジェクトのカテゴリを拒否するかをクリックして、 **Active**カテゴリ フォルダーの横にあるフィールドです。  
  
    色の設定の定義を表示する をクリックして、**凡例**ボタンをクリックします。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
## <a name="next-step"></a>次の手順  
  
-   移行プロセスの次の手順が、 [SQL Server のインスタンスへの接続](http://msdn.microsoft.com/en-us/1b2a8059-1829-4904-a82f-9c06de1e245f)です。  
  
## <a name="see-also"></a>参照  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
