---
title: "SSMA for Access(AccessToSQL) の新機能 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
caps.latest.revision: 37
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a435479b9cad332215b1f44f7d881f5055b2fefd
ms.openlocfilehash: 5cc5b9bf49c28b298570e0c867c5b03e8ad99c47
ms.contentlocale: ja-jp
ms.lasthandoff: 11/08/2017

---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>SSMA for Access (AccessToSQL) の新機能
このトピックでは、各リリースでのアクセスの変更の SSMA が一覧表示します。  

## <a name="ssma-v76"></a>SSMA v7.6
SSMA for Access の v7.6 リリースの品質、および変換のメトリックを向上する対象となる修正プログラムと SQL Server 2017 (パブリック プレビュー) のサポートが拡張されました。 Windows および Linux での SQL Server 2017 のサポートは、パブリック プレビューではの運用環境の移行は使用できません。

> [!IMPORTANT]
> SSMA v7.4 とそれ以降のバージョンでは、.Net 4.5.2 は、のインストール前提条件、およびツールの 32 ビット バージョンは廃止されました。

## <a name="ssma-v75"></a>SSMA v7.5
SSMA for Access の v7.5 リリースは、障碍の大きいアクセシビリティを確認するいくつかの機能強化で強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.5 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。

## <a name="ssma-v74"></a>SSMA v7.4
SSMA for Access の v7.4 リリースには、次の変更が含まれています。
- **クエリのタイムアウト**オプションは、ソースとターゲットのスキーマ オブジェクトの検出中に使用できるようになりました。
![query timeout オプション](../media/query-timeout_red.png)

- 品質と変換のメトリックは、お客様のフィードバックに基づいて、対象となる修正プログラムが強化されています。

> [!IMPORTANT]
> .Net 4.5.2 は、SSMA v7.4 をインストールするための事前必須コンポーネントです。 さらに、v7.4 から始まり、SSMA の 32 ビット バージョンは廃止されています。

## <a name="ssma-v73"></a>SSMA v7.3
SSMA for Access の v7.3 リリースには、次の変更が含まれています。
- 改善の品質、および変換のメトリックを対象となる修正プログラムがお客様のフィードバックに基づきます。
- SSMA 拡張性フレームワークが、次の項目を使用して公開します。
  - SQL Server Data Tools (SSDT) プロジェクトに機能をエクスポートします。
    -   SSMA から SSDT プロジェクトにスキーマ スクリプトをエクスポートできます。 スキーマ スクリプトを使用して、追加のスキーマ変更を加えるし、データベースを展開することができます。
![SSDT プロジェクト コマンドとして保存します。](../media/export-schema-scripts_red.png)

  - カスタム変換を実行するの SSMA で利用できるライブラリ。
    - これでカスタム構文変換および SSMA によって処理されなかったいた変換を処理できるコードを構築できます。
      - カスタムのコンバーターを作成する方法の手順については、このブログの投稿[変換機能を拡張する SQL Server Migration Assistant の](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)します。
      - この変換用のサンプル プロジェクトをダウンロードできる[ブログの投稿](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/)です。

## <a name="ssma-v72"></a>SSMA v7.2
SSMA for Access の v7.2 リリースには、次の変更が含まれています。
- 改善の品質、および変換のメトリックを対象となる修正プログラムがお客様のフィードバックに基づきます。
- 製品利用統計情報をお客様の問題をトラブルシューティングし、SSMA の換算率を向上させる優れたデータ ポイントを提供する拡張機能です。

## <a name="ssma-v71"></a>SSMA v7.1
SSMA for Access の v7.1 リリースには、次の変更が含まれています。
- Windows と Linux CTP1 では、SQL Server 2017 は、移行のサポート対象のターゲット プラットフォームではようになりました。 この機能は、technical preview では、SQL の対象サーバーにスキーマとデータの移動をサポートしています。
- SSMA は、使用可能になるとすぐには、SSMA の最新バージョンをダウンロードする自動更新をサポートします。
- SSMA インストール可能なバイナリは、Windows インストーラー パッケージ ファイル (.msi) により配信されるようになりました。

**リソース**

[SQL Server Migration Assistant の変換機能を拡張します。](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)
  
## <a name="may-2016"></a>2016 年 5 月  
SSMA for Access の 2016 年 5 月リリースには、次の変更が含まれています。  
  
-  SQL Server 2016 用の正式なサポートが追加されました
-  .Net 2.0 のインストーラーのチェックを削除します。
-  [保存] プロジェクト"固定と SSMA コンソールの「プロジェクトを開く」コマンド。
-  SSMA コンソールの"securepassword"コマンドを固定します。
-  初期読み込みのためのオブジェクトのカウントを修正しました。
-  テーブルのデータのアクセス用の UI タブの読み込みを固定します。
-  グローバル設定のバグを修正します。 
   
## <a name="march-2016"></a>2016 年 3 月  
SSMA for Access の 2016 年 3 月のプレビュー リリースには、次の変更が含まれています。  
  
-  SQL Server 2016 への移行のサポートが追加されました。  
   
## <a name="january-2016"></a>2016 年 1 月  
SSMA for Access の 2016 年 1 月メンテナンス リリースには、次の変更が含まれています。  
  
-  GUID フィールド (RFC 3894811) の既定の無効な関数を固定します。  
-  SQL データベース (Azure) (RFC 4919573) レコードをインポートする固定のハングアップします。  
-  SSMA (RFC 5706203) するには、ログ メニュー項目を追加したビューです。  
-  追加された製品利用統計情報。  
  
## <a name="july-2014"></a>2014 年 7 月  
SSMA for Access の 2014 年 7 月リリースには、次の変更が含まれています。  
  
-   Azure SQL DB コードの変換が向上します。  
-   Azure SQL DB をサポートするためにスキーマに拡張機能パックの機能を移動します。  
-   10 k オブジェクトを含むデータベースのテストのパフォーマンスを向上します。  
-   多数のオブジェクトを処理するための追加の UI 機能強化。  
-   (したがって、変換で無視する) に「既知」の LOB スキーマの強調表示のサポートを追加します。  
-   変換速度の向上を追加します。
-   オブジェクトを表示するためのサポートが追加されましたが、UI にカウントします。
-   25% 以上のレポート サイズ。
-   未解析のコンス トラクターに対して改善されたエラー メッセージ。  
  
## <a name="april-2014"></a>2014 年 4 月  
SSMA for Access の 2014 年 4 月リリースには、次の変更が含まれています。  
  
-   MS SQL Server 2014 のサポートを追加します。  
-   Azure への変換に関する修正されたバグはします。  
-   IE 10 で非表示レポート ページに関する修正されたバグはします。  
  
## <a name="january-2012"></a>2012 年 1 月  
SSMA for Access の 2012 年 1 月リリースには、次の変更が含まれています。  
  
-   MS アクセスでは、移行後にテーブルがリンクされているので、ユーザー名とパスワードを保持されないするオプションが用意されています。  
-   No Action を循環参照の連鎖操作を設定します。  
-   指定の循環参照の連鎖操作を示す適切なメッセージは、No Action に設定されています。  
  
## <a name="july-2011"></a>2011 年 7 月  
SSMA for Access の 2011 年 7 月リリースには、次の変更が含まれています。  
  
-   エラー報告データの移行中の強化。  
  
## <a name="april-2011"></a>2011 年 4 月  
SSMA for Access の 2011 年 4 月リリースには、次の変更が含まれています。  
  
-   "SSMA のアクセス権の"をサポートしているインストール可能な 1 つの追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2005 では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] "Denali"と Azure SQL です。  
-   接続する機能が追加されました[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]"Denali"  
-   旧バージョンとの互換性のため追加の SSMA for Access コンソールのバージョンをサポートします。 SSMA v5.0 以前のバージョンで作成されたプロジェクトを開くことができます。
-   SSMA 製品の以前のバージョンと SSMA v5.0 製品サイド バイ サイド (SxS) をインストールする機能が追加されました。  
  
## <a name="july-2010"></a>2010 年 7 月  
SSMA for Access の 2010 年 7 月リリースには、次の変更が含まれています。  
  
-   SQL Server 2008 R2 と Azure SQL への移行のサポートが追加されました。
-   SQL Server と Azure SQL の両方にセキュリティで保護された接続を追加します。  
-   Access 2010 データベースのサポートを追加します。
-   コマンドラインの実行用の新しい SSMA コンソール アプリケーションを追加します。
-   SQL Server DateTime2 データ型のサポートを追加します。
  
## <a name="june-2008"></a>2008 年 6 月  
SSMA for Access の 2008 年 6 月リリースには、次の変更が含まれています。  
  
-   Access 2007 データベースのサポートを追加します。  
  
## <a name="may-2007"></a>2007 年 5 月  
SSMA for Access の 2007 年 5 月リリースには、次の変更が含まれています。  
  
-   ワークグループのポリシーを使用して Access データベースのサポートを追加します。  
-   SQL Server メタデータ エクスプ ローラーから変換されたオブジェクトを削除する機能を提供します。  
-   SQL Server のユーザーが入力したコメントのサポートを追加では、SQL モードが書式設定されます。  
-   オブジェクトへの変換に追加された機能強化。  
  
## <a name="november-2006"></a>2006 年 11 月  
SSMA for Access の 2006 年 11 月リリースには、次の変更が含まれています。  
  
-   アクセスを 1 つのデータベースの移行を案内する新しいデータベース移行ウィザードを追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
-   新しい変換、読み込みを追加し、Access データベースに変換する移行コマンド、変換後にオブジェクトを読み込みます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]へのデータを移行および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]すべて 1 つの手順でします。  
-   強化されたクエリの移行。 移行のクエリを実行して、これで、変換がよりをビューにクエリを選択します。 詳細については、次を参照してください。[データベース オブジェクトの変換へのアクセス](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)です。  
-   テーブルとインデックスのプロパティを編集する機能を追加、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **テーブル**タブです。  
-   新しいグローバル設定を追加します。  
    -   エディター ウィンドウ内の行番号の表示にすることもできます。  
    -   SSMA 重複するオブジェクトを交換を要求するメッセージを構成したりできますかは、スキーマの変換中に重複するオブジェクトを置き換えます。  
-   SSMA では、複雑なクエリには、ワイルドカードが含まれている場合に、警告が表示されるかどうかを指定できる新しい変換オプションを追加します。  
  
## <a name="july-2006"></a>2006 年 7 月  
SSMA for Access の 2006 年 7 月リリースでは、最初のリリースをでした。

