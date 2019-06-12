---
title: SSMA for Access (AccessToSQL) における新 |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 06/11/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
author: HJToland3
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0f0084f93fa648e5db79ef70dd5f05a259b94b67
ms.sourcegitcommit: 40e55e55a73e39d447da87d9178f2b6067f39c6f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "66841117"
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>SSMA for Access (AccessToSQL) の新機能新機能

この記事では、アクセスの変更を各リリースでの SQL Server Migration Assistant (SSMA) が一覧表示します。  

## <a name="ssma-v82"></a>SSMA v8.2

SSMA for Access の v8.2 リリースは、な品質と変換のメトリックを向上させるように設計された、対象となる修正プログラムが強化されています。

> [!NOTE]
> 自動更新に関する既知の問題は、v8.2 を SSMA v8.1 から更新プログラムのエラーを発生可能性があります。 このエラーが発生した場合は、新しいバージョンをダウンロードして手動でインストールしてください。

> [!IMPORTANT]
> SSMA v7.4 と以降のバージョンでは、.Net 4.5.2 は、インストールの前提条件です。

## <a name="ssma-v81"></a>SSMA v8.1

SSMA for Access の v8.1 リリースは、な品質と変換のメトリックを向上させるように設計された、対象となる修正プログラムが強化されています。

> [!NOTE]
> 自動更新に関する既知の問題は、v8.1 を SSMA バージョン 8.0 から更新プログラムのエラーを発生可能性があります。 このエラーが発生した場合は、新しいバージョンをダウンロードして手動でインストールしてください。

## <a name="ssma-v80"></a>SSMA v8.0

SSMA for Access のバージョン 8.0 リリースは、な品質と変換のメトリックを強化するために対象となる修正プログラムが強化されています。 このリリースでは、次の新機能も提供します。

* サポート**Azure SQL Database マネージ インスタンス**ターゲットとして。 Azure SQL Database マネージ インスタンスを対象とする新しいプロジェクトを作成できます。

  ![SQL DB MI プロジェクト](../media/ssma-newproject-sqldbmi.png)

* 変換後**修正アドバイザー**します。 詳細については、[ここ](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/)します。

* 予備データベース/スキーマの選択。

    ソースへの接続時にユーザーを関心のあるデータベース/スキーマ選択できます。 移行を計画する、スキーマだけを選択すると、初期接続時の時間を節約し、SSMA の全体的なパフォーマンスを向上します。

   ![SSMA フィルター オブジェクト](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

SSMA for Access の v7.10 リリースに追加のセキュリティとプライバシーの保護をグローバル要件の変更を満たすために提供するように設計対象の修正が強化されます。

## <a name="ssma-v79"></a>SSMA v7.9

SSMA for Access の v7.9 リリースには、次の変更が含まれています。

* 品質と変換のメトリックを向上させる対象となる修正します。
* データ型マッピングとプロジェクトの環境設定を変更するコマンドラインの SSMA でサポートします。
* SSMA で Azure SQL Database の接続ダイアログが、完全修飾サーバー名を指定することも変更されました。 SSMA の以前のバージョンで、Azure SQL Database のプレフィックスは、プロジェクト設定内で明示的に説明する必要があります。

## <a name="ssma-v78"></a>SSMA v7.8

SSMA for Access の v7.8 リリースには、次の変更が含まれています。

* プロジェクトの設定で強調表示されている型のマッピングを変更します。
* ユーザーがテレメトリを無効にする機能。

## <a name="ssma-v77"></a>SSMA v7.7

SSMA for Access の v7.7 リリースには、次の変更が含まれています。

* 品質と変換のメトリックを向上させる対象となる修正します。
* SSMA for Access の 32 ビット バージョンは戻るには、要望に基づき、です。 (V7.4) の前に、前の実装と比較して、2 つのインストーラー パッケージがあるが、並行してインストールことはできません。 その結果がある場合、接続コンポーネントに基づいて最も適切なバージョンを選択する必要があります。 可能であれば、64 ビット バージョンを使用することをお勧めは常にします。

## <a name="ssma-v76"></a>SSMA v7.6

SSMA for Access の v7.6 リリース品質と変換のメトリックを向上させる修正プログラムを対象となると SQL Server 2017 (パブリック プレビュー) のサポートが強化されます。 Windows および Linux 上の SQL Server 2017 のサポートはパブリック プレビューであり、運用環境の移行のために使用しないでください。

## <a name="ssma-v75"></a>SSMA v7.5

SSMA for Access の v7.5 リリースで障碍を持つユーザーのアクセシビリティを確保するいくつかの機能が強化されます。

## <a name="ssma-v74"></a>SSMA v7.4

SSMA for Access の v7.4 リリースには、次の変更が含まれています。

* **クエリ タイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。

  ![query timeout オプション](../media/query-timeout_red.png)

* 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

  > [!IMPORTANT]
  > .Net 4.5.2 は SSMA v7.4 をインストールするための前提条件です。 さらに、v7.4 以降では、SSMA の 32 ビット バージョンは廃止されました。

## <a name="ssma-v73"></a>SSMA v7.3

SSMA for Access の v7.3 リリースには、次の変更が含まれています。

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

SSMA for Access の v7.2 リリースには、次の変更が含まれています。

* お客様からのフィードバックに基づいて対象となる修正プログラムで強化された品質と変換メトリック。
* 顧客の問題をトラブルシューティングし、SSMA のコンバージョン率を向上させるより良いデータ ポイントを提供するテレメトリの機能強化。

## <a name="ssma-v71"></a>SSMA v7.1

SSMA for Access の v7.1 リリースには、次の変更が含まれています。

* Windows と Linux CTP1 で SQL Server 2017 は、移行のサポートされているターゲット プラットフォームではようになりました。 この機能は、technical preview では、SQL の対象サーバーにスキーマとデータの移動をサポートしています。
* SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
* SSMA のインストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) が配信されるようになりました。

## <a name="may-2016"></a>2016 年 5 月

SSMA for Access の 2016 年 5 月リリースには、次の変更が含まれています。  
  
* SQL Server 2016 用公式サポートが追加されました
* .Net 2.0 のインストーラーのチェックを削除します。
* プロジェクト"保存"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
* SSMA コンソールの"securepassword"コマンドを修正しました。
* オブジェクトの初期読み込みのカウントを修正しました。
* テーブルのデータがアクセスするための UI タブの読み込みを修正しました。
* グローバル設定でバグを修正しました。 

## <a name="march-2016"></a>2016 年 3 月

SSMA for Access の 2016 年 3 月のプレビュー リリースでは、SQL Server 2016 への移行のサポートを追加します。  

## <a name="january-2016"></a>2016 年 1 月

SSMA for Access の 2016 年 1 月のメンテナンス リリースには、次の変更が含まれています。  
  
* GUID フィールド (RFC 3894811) の既定の無効な関数を固定します。  
* SQL Database (Azure) (RFC 4919573) レコードをインポートする固定のハングアップします。  
* 追加の表示 メニュー項目をログ、SSMA (RFC 5706203) にします。  
* 追加された製品利用統計情報。
  
## <a name="july-2014"></a>2014 年 7 月

SSMA for Access の 2014 年 7 月リリースには、次の変更が含まれています。  
  
* Azure SQL DB コード変換の改善。  
* 拡張機能パックの機能を Azure SQL DB をサポートするスキーマに移動します。  
* 10 k オブジェクトとデータベースのテストのパフォーマンスを向上します。  
* 多数のオブジェクトを処理するための追加の UI 機能強化。  
* (したがって、これらは、変換で無視されます) の「既知」の LOB スキーマの強調表示のサポートが追加されました。  
* 変換速度の向上を追加します。
* UI でオブジェクトを表示するためのサポートが追加されましたがカウントされます。
* 25% 以上削減レポート サイズ。
* 未解析のコンス トラクターに対して改善されたエラー メッセージ。  
  
## <a name="april-2014"></a>2014 年 4 月

SSMA for Access の 2014 年 4 月リリースには、次の変更が含まれています。  
  
* MS SQL Server 2014 のサポートが追加されました。
* Azure への変換に関するバグを固定します。  
* IE 10 で非表示レポート ページに関するバグを固定します。  
  
## <a name="january-2012"></a>2012 年 1 月

SSMA for Access の 2012 年 1 月リリースには、次の変更が含まれています。  
  
* MS アクセス リンク テーブルに移行後のないユーザー名とパスワードを保持するオプションが用意されています。  
* No Action に循環参照の連鎖操作を設定します。  
* 指定の循環参照の連鎖操作を示す適切なメッセージは、No Action に設定されています。  
  
## <a name="july-2011"></a>2011 年 7 月

SSMA for Access の 2011 年 7 月リリースでは、エラー報告データ移行中の強化を追加します。  
  
## <a name="april-2011"></a>2011 年 4 月

SSMA for Access の 2011 年 4 月リリースには、次の変更が含まれています。  
  
* "SSMA for Access の"をサポートするインストール可能な 1 つの追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] "Denali"と Azure SQL。  
* 接続する機能が追加されました[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]"Denali"  
* 旧バージョンとの互換性のため追加の SSMA for Access コンソールのバージョンをサポートします。 SSMA v5.0 を以前のバージョンで作成されたプロジェクトを開くことができます。
* SSMA 製品の以前のバージョンでの SSMA v5.0 製品サイド バイ サイド (SxS) をインストールする機能が追加されました。  
  
## <a name="july-2010"></a>2010 年 7 月  
SSMA for Access の 2010 年 7 月リリースには、次の変更が含まれています。  
  
* SQL Server 2008 R2 と Azure SQL への移行のサポートが追加されました。
* SQL Server と Azure SQL の両方をセキュリティで保護された接続を追加します。  
* Access 2010 データベースのサポートが追加されました。
* コマンドラインの実行用の新しい SSMA コンソール アプリケーションを追加します。
* SQL Server DateTime2 データ型のサポートが追加されました。
  
## <a name="june-2008"></a>2008 年 6 月

SSMA for Access の 2008 年 6 月リリースでは、Access 2007 データベースのサポートを追加します。  
  
## <a name="may-2007"></a>2007 年 5 月

SSMA for Access の 2007 年 5 月リリースには、次の変更が含まれています。  
  
* ワークグループのポリシーを使用する Access データベースのサポートが追加されました。  
* SQL Server メタデータ エクスプ ローラーから変換されたオブジェクトを削除する機能を提供します。  
* SQL Server でのユーザーが入力したコメントのサポートを追加では、SQL モードが書式設定されます。  
* オブジェクトへの変換で追加された機能を強化します。  
  
## <a name="november-2006"></a>2006 年 11 月

SSMA for Access の 2006 年 11 月リリースには、次の変更が含まれています。  
  
* 新しいデータベースの移行ウィザードへのアクセスを 1 つのデータベースの移行をガイドする追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
* 新しい変換、読み込みを追加し、Access データベースに変換する移行コマンドに変換されたオブジェクトを読み込みます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]へのデータを移行したり[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]すべて 1 つの手順でします。  
* 強化されたクエリの移行。 移行をクエリに変換しますをビューにクエリをより選択するようになりました。 詳細については、次を参照してください。 [Access データベース オブジェクトの変換](converting-access-database-objects-accesstosql.md)します。  
* テーブルとインデックスのプロパティを編集する機能を追加、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **テーブル**タブ。  
* 新しいグローバル設定を追加するには。
  * エディターのウィンドウで行番号を表示できます。  
  * 重複するオブジェクトの置き換えを確認する SSMA を構成したり、スキーマの変換中に重複するオブジェクトを置き換えますかできます。  
* SSMA では、複雑なクエリには、ワイルドカードが含まれている場合に、警告が表示されるかどうかを指定できる変換オプションが新たに追加します。  
  
## <a name="july-2006"></a>2006 年 7 月

SSMA for Access の 2006 年 7 月リリースでは、最初のリリースをでした。
