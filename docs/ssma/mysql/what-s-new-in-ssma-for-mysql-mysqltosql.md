---
title: SSMA for MySQL (MySQLToSql) における新 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 06/11/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
author: HJToland3
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5f3ea9905f0a44e7863154b93283ea8ef2f49f7b
ms.sourcegitcommit: 40e55e55a73e39d447da87d9178f2b6067f39c6f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "66841065"
---
# <a name="whats-new-in-ssma-for-mysql-mysqltosql"></a>SSMA for MySQL の新機能 (MySqlToSql)

この記事では、各リリースでの MySQL の変更を SQL Server Migration Assistant (SSMA) が一覧表示します。

## <a name="ssma-v82"></a>SSMA v8.2

品質と変換のメトリック、ほかの修正を強化するために修正プログラムの対象となるセットでの SSMA for MySQL の v8.1 リリースが強化されます。

* データの移行後の無効化された非クラスター化インデックスの問題。
* .NET Framework のサイレント インストール時に検出します。
* 新しいバージョンをダウンロードするときに発生する断続的なクラッシュします。

> [!NOTE]
> 自動更新に関する既知の問題は、v8.2 を SSMA v8.1 から更新プログラムのエラーを発生可能性があります。 このエラーが発生した場合は、新しいバージョンをダウンロードして手動でインストールしてください。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v81"></a>SSMA v8.1

品質と変換のメトリックを向上させるように設計された、対象となる修正プログラムでの SSMA for MySQL の v8.1 リリースが強化されます。

> [!NOTE]
> 自動更新に関する既知の問題は、v8.1 を SSMA バージョン 8.0 から更新プログラムのエラーを発生可能性があります。 このエラーが発生した場合は、新しいバージョンをダウンロードして手動でインストールしてください。

## <a name="ssma-v80"></a>SSMA v8.0

品質と変換のメトリックを強化するために対象となる修正プログラムでの SSMA for MySQL のバージョン 8.0 リリースが強化されます。 このリリースでは、次の新機能も提供します。

* サポート**Azure SQL Database マネージ インスタンス**ターゲットとして。 Azure SQL Database マネージ インスタンスを対象とする新しいプロジェクトを作成できます。

  ![SQL DB MI プロジェクト](../media/ssma-newproject-sqldbmi.png)

* 変換後**修正アドバイザー**します。 詳細については、[ここ](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/)します。

* 予備データベース/スキーマの選択。

  ソースへの接続時にユーザーを関心のあるデータベース/スキーマ選択できます。 移行を計画する、スキーマだけを選択すると、初期接続時の時間を節約し、SSMA の全体的なパフォーマンスを向上します。

  ![SSMA フィルター オブジェクト](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

SSMA の MySQL の v7.10 リリースには、次の変更が含まれています。

* 対象となる修正プログラムが追加のセキュリティとプライバシーの保護をグローバル要件の変更を満たすために提供するように設計します。
* 関数の名前と引数リストとの間の空白文字の変換の修正プログラムです。

## <a name="ssma-v79"></a>SSMA v7.9

SSMA の MySQL の v7.9 リリースには、次の変更が含まれています。

* 品質と変換のメトリックを向上させる対象となる修正します。
* MySQL から Azure SQL Database への移行の空間データ型の部分的にサポートします。
* データ型マッピングとプロジェクトの環境設定を変更するコマンドラインの SSMA でサポートします。
* 移行のサポートを SQL Server Integration Services (SSIS) を使用してデータ。 スキーマを変換した後を右クリック コンテキスト メニュー オプションを使用して、SSIS パッケージを作成することができます。
* SSMA で Azure SQL Database の接続ダイアログが、完全修飾サーバー名を指定することも変更されました。 SSMA の以前のバージョンで、Azure SQL Database のプレフィックスは、プロジェクト設定内で明示的に説明する必要があります。

## <a name="ssma-v78"></a>SSMA v7.8

SSMA の MySQL の v7.8 リリースには、次の変更が含まれています。

* プロジェクトの設定で強調表示されている型のマッピングを変更します。
* ユーザーがテレメトリを無効にする機能。

## <a name="ssma-v77"></a>SSMA v7.7

SSMA の MySQL の v7.7 リリースには、次の変更が含まれています。

* SSMA for MySQL は、品質と変換のメトリックを向上させる対象となる修正プログラムで拡張されています。
* SSMA for MySQL の 32 ビット バージョンは戻るには、要望に基づき、です。 (V7.4) の前に、前の実装と比較して、2 つのインストーラー パッケージがあるが、並行してインストールことはできません。 その結果がある場合、接続コンポーネントに基づいて最も適切なバージョンを選択する必要があります。 可能であれば、64 ビット バージョンを使用することをお勧めは常にします。
* SSMA for MySQL では、ODBC 接続文字列の接続モードでの MySQL を使用した互換性のあるサードパーティ製 ODBC ドライバーを使用できるようにできるようになりました。

## <a name="ssma-v76"></a>SSMA v7.6

MySQL 用の SSMA v7.6 リリース品質と変換のメトリックを向上させる修正プログラムを対象となると SQL Server 2017 (パブリック プレビュー) のサポートが強化されました。 Windows および Linux 上の SQL Server 2017 のサポートはパブリック プレビューであり、運用環境の移行のために使用しないでください。

## <a name="ssma-v75"></a>SSMA v7.5

障碍を持つユーザーのアクセシビリティを確認します。 いくつかの機能強化の SSMA for MySQL の v7.5 リリースが強化されました。

## <a name="ssma-v74"></a>SSMA v7.4

MySQL 用の SSMA の v7.4 リリースには、次の変更が含まれています。

* **クエリ タイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。

    ![query timeout オプション](../media/query-timeout_red.png)
* 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は SSMA v7.4 をインストールするための前提条件です。 さらに、v7.4 以降では、SSMA の 32 ビット バージョンは中止されています。

## <a name="ssma-v73"></a>SSMA v7.3

MySQL 用の SSMA の v7.3 リリースには、次の変更が含まれています。

* お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
* SSMA 拡張性フレームワークは、次のものを使用して公開:
  * SQL Server Data Tools (SSDT) プロジェクトにエクスポートする機能。
    * SSMA から SSDT プロジェクトにスキーマ スクリプトをエクスポートできます。 スキーマ スクリプトを使用して、追加のスキーマを変更して、データベースをデプロイすることができます。

      ![SSDT プロジェクト コマンドとして保存します。](../media/export-schema-scripts_red.png)
  * カスタム変換を実行するために、SSMA で使用できるライブラリ。
    * 構文のカスタム変換および変換 SSMA によって処理されなかった以前に対応するコードを作成します。
      * カスタムのコンバーターを作成する方法の手順については、このブログ投稿「[変換機能を拡張する SQL Server Migration Assistant の](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)します。
      * これからの変換のサンプル プロジェクトをダウンロード[ブログの投稿](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/)します。

## <a name="ssma-v72"></a>SSMA v7.2

SSMA の MySQL の v7.2 リリースには、次の変更が含まれています。

* お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
* 顧客の問題をトラブルシューティングし、SSMA のコンバージョン率を向上させるより良いデータ ポイントを提供するテレメトリの機能強化。

## <a name="ssma-v71"></a>SSMA v7.1

SSMA の MySQL の v7.1 リリースには、次の変更が含まれています。

* Windows と Linux CTP1 で SQL Server 2017 は、移行のサポートされているターゲット プラットフォームではようになりました。 この機能は、technical preview ではあり、対象の SQL サーバーにスキーマとデータの移動を許可します。
* SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
* SSMA のインストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) が配信されるようになりました。

## <a name="may-2016"></a>2016 年 5 月  
MySQL 用の SSMA の 2016 年 5 月リリースには、次の変更が含まれています。

* SQL Server 2016 のサポートが追加されました。
* 強化されたパーサーと競合回避モジュール。
* .Net 2.0 のインストーラーのチェックを削除します。
* 更新された拡張機能パックの依存関係から .Net 3.5 を .Net 4.0 にします。
* MySql の既定の固定 BigInt 型のマッピング。
* プロジェクト"保存"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
* SSMA コンソールの"securepassword"コマンドを修正しました。
* オブジェクトの初期読み込みのカウントを修正しました。
* 固定 MsSql オブジェクトを読み込みます。
* グローバル設定でバグを修正しました。

## <a name="march-2016"></a>2016 年 3 月

SSMA for MySQL の 2016 年 3 月プレビューのリリースでは、SQL Server 2016 への移行のサポートを追加します。 
  
## <a name="january-2016"></a>2016 年 1 月

MySQL の SSMA の 2016 年 1 月のメンテナンス リリースには、次の変更が含まれています。  

* 追加の表示 メニュー項目をログ、SSMA (RFC 5706203) にします。  
* 追加された製品利用統計情報。  
  
## <a name="july-2014"></a>2014 年 7 月

MySQL 用の SSMA の 2014 年 7 月リリースには、次の変更が含まれています。  
  
* Azure SQL DB コード変換の改善。 
* 拡張機能パックの機能は、Azure SQL DB をサポートするために、スキーマに移動します。  
* パフォーマンスの向上は、10 k を超えるデータベースのオブジェクトをテストします。  
* 多数のオブジェクトを処理するための UI 機能強化。  
* (したがって、これらは、変換で無視されます)、「既知」の LOB スキーマの強調表示します。  
* 速度の向上を変換します。  
* UI 内のオブジェクトの数を表示します。  
* 25% 以上のレポート サイズの縮小します。  
* 未解析のコンス トラクターに対して改善されたエラー メッセージ。  
  
## <a name="april-2014"></a>2014 年 4 月

MySQL 用の SSMA の 2014 年 4 月リリースには、次の変更が含まれています。  
  
* MS SQL Server 2014 のサポートが追加されました。  
* Azure への変換に関する修正されたバグ  
* IE 10 で非表示レポート ページに関するバグを固定します。  
  
## <a name="july-2011"></a>2011 年 7 月

MySQL 用の SSMA の 2011 年 7 月リリースには、次の変更が含まれています。  
  
* 制限の変換がサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]"Denali"のオフセットします。  
* レポート データの移行中にエラーを改善しました。  
  
## <a name="april-2011"></a>2011 年 4 月

MySQL 用の SSMA の 2011 年 4 月リリースには、次の変更が含まれています。  
  
* 1 つの"SSMA for MySQL"をサポートするインストール可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali"と Azure SQL。  
* 接続する機能[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]"Denali"  
* データの並列移行のサポート、強化されたクライアント側のデータ移行エンジン。  
* 強化されたデータの移行とパフォーマンスを単純な一括復旧モデルが記録されます。  
* SSMA for MySQL コンソールのバージョンでは、旧バージョンとの互換性をサポートします。 SSMA v5.0 を以前のバージョンで作成されたプロジェクトを開くことができます。  
* SSMA for MySQL v5.0 製品には、SSMA 製品の旧バージョンとサイド バイ サイド (SxS) がインストールされています。  
  
## <a name="july-2010"></a>2010 年 7 月

MySQL 用の SSMA の 2010 年 7 月リリースには、次の機能が含まれています。  
  
1. **ユーザー インターフェイスの機能強化:**  
  
    * 'SQL モード' の MySQL データベースのオブジェクト タブ  
    * MySQL データベース オブジェクトの [設定] タブ  
    * MySQL テーブルの 'データ' タブ  
    * 変換と移行のページで、更新されたプロジェクトの設定  
    * テーブル レベルで [データ移行の設定]  
  
2. **MySQL および SQL Server に接続するための機能強化:**  
  
    * MySQL の SSL 接続  
    * SQL Server で暗号化された接続  
  
3. **MySQL Metabase Explorer の機能強化:**  
  
    * MySQL データベースのすべてのオブジェクトと、それぞれのタブを読み込んでいます。  
  
4. **オブジェクトへの変換の機能強化:**
  
    * プロシージャ、関数、ビュー、トリガー、およびステートメント - MySQL メタベース オブジェクトが変換されます。  
    * テーブル内の空間データ型の制限付きのサポート。
    * MySQL の機能を SQL Server ストアド プロシージャに変換するオプション  
    * オブジェクトの変換中に SQL モードと文字セットのマッピングを適用するオプション  
  
5. **データ移行の機能強化:**  
  
    * サーバー側とクライアント側のデータ移行のエンジンの両方を使用してデータ移行のサポート  
    * 空間データの移行のサポート  
    * カスタムの SQL テーブルのデータの移行  
  
6. **SSMA for MySQL コンソール:**  
  
    * SSMA for MySQL のコンソール機能のサポート  
    * スクリプト レベルのインターフェイスのサポート  
  
## <a name="january-2010"></a>2010 年 1 月

MySQL 用の SSMA の 2010 年 1 月リリースは、最初のリリースでした。 次の機能が含まれています。 
  
* 両方への移行のサポートを追加でオンプレミス SQL Server と Azure SQL。  
  
* **スナップショットの機能:** スキーマとデータの移行 MySQL テーブル/インデックスと制約の。
