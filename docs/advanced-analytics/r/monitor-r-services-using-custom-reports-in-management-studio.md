---
title: "Management Studio でカスタム レポートを使用して R Services を監視する | Microsoft Docs"
ms.custom: 
ms.date: 02/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5933c72c-ba63-4966-b882-75719ef8428e
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 14f6d6d7373afd452f06acae43f7023de136bc71
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="monitor-r-services-using-custom-reports-in-management-studio"></a>Management Studio でカスタム レポートを使用して R Services を監視する
SQL Server R Services を管理しやすくするために、製品チームでは多くのサンプル カスタム レポートを用意しています。これらを Server Management Studio に追加して、次のような R Services の詳細を表示することができます。

- アクティブな R セッションのリスト
- 現在のインスタンスの R 構成
- R ランタイムの実行統計
- R Services の拡張イベント リスト
- 現在のインスタンスにインストールされている R パッケージのリスト

このトピックでは、レポートのインストールおよび使用方法について説明します。 Management Studio のカスタム レポートの詳細については、「 [Management Studio におけるカスタム レポート](~/ssms/object/custom-reports-in-management-studio.md)」を参照してください。

## <a name="how-to-install-the-reports"></a>レポートのインストール方法

レポートは SQL Server Reporting Services を使用するように設計されていますが、SQL Server Management Studio から直接使用することができます。インスタンスに Reporting Services がインストールされていない場合でも同じです。 

これらのレポートを使用する場合は、次のようにします。

* SQL Server 製品サンプルの GitHub リポジトリから RDL ファイルをダウンロードします。
* SQL Server Management Studio で使用されるカスタム レポート フォルダーにファイルを追加します。
* SQL Server Management Studio でレポートを開きます。


### <a name="step-1-download-the-reports"></a>手順 1. サンプルのダウンロード

1. [SQL Server の製品サンプル](https://github.com/Microsoft/sql-server-samples)を含む GitHub リポジトリを開き、このページからサンプル レポートをダウンロードします。 

   + [SSMS カスタム レポート](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/ssms-custom-reports)
      
2. サンプルをダウンロードする場合、GitHub にログインし、サンプルのローカル分岐を作成することもできます。 

### <a name="step-2-copy-the-reports-to-management-studio"></a>手順 2. Management Studio へのレポートのコピー

3. SQL Server Management Studio で使用されるカスタム レポート フォルダーを見つけます。 既定では、カスタム レポートは次のフォルダーに格納されます。
    
   `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

   ただし、別のフォルダーを指定したり、サブフォルダーを作成したりすることもできます。

4. *.RDL ファイルをカスタム レポート フォルダーにコピーします。


### <a name="step-3-run-the-reports"></a>手順 3. レポートの実行

5. Management Studio で、レポートを実行するインスタンスの **[データベース]** ノードを右クリックします。
6. **[レポート]**、 **[カスタム レポート]**の順にクリックします。 
7. **[ファイルを開く]** ダイアログ ボックスで、カスタム レポート フォルダーを見つけます。
8. ダウンロードした RDL ファイルを選択し、 **[開く]**をクリックします。

> [!IMPORTANT]
> 高 DPI または 1080 p を超える解像度のディスプレイ デバイスを持つ一部のコンピューターや、一部のリモート デスクトップ セッションでは、これらのレポートは使用できません。 SSMS のレポート ビューアー コントロールには、レポートのクラッシュの原因となるバグがあります。  


## <a name="report-list"></a>レポート リスト

現在、GitHub の製品サンプル リポジトリには、SQL Server R Services 用の以下のレポートが含まれています。

+ **R Services - Active Sessions**

  このレポートを使用して、現在、SQL インスタンスに接続し、R ジョブを実行しているユーザーを表示します。 
  
+ **R Services - Configuration**

  このレポートを使用して、R Services の R ランタイムと構成のプロパティを表示します。 レポートでは、再起動が必要かどうかが示され、必要なネットワーク プロトコルが確認されます。 
  
  SQL 計算コンテキストで R を実行する場合は、暗黙の認証が必要になります。これを確認するために、レポートでは、グループ SQLRUserGroup のデータベース ログインが存在するかどうかが確認されます。

  > [!NOTE]
  > これらのフィールドの詳細については、「 [Package metadata](http://r-pkgs.had.co.nz/description.html)」 (パッケージ メタデータ) (作成者: Hadley Wickam) を参照してください。 たとえば、導入された R ランタイムの *[ニックネーム]* フィールドは、各リリースを区別するのに役立ちます。 

 + **R Services - Configure Instance** 

   このレポートは、インストール後に R Services を構成する場合に役立ちます。 R Services が正しく構成されていない場合は、前のレポートから実行できます。
 
+ **R Services - Execution Statistics**

  このレポートを使用して、R Services の実行統計を表示します。 たとえば、実行された R スクリプトの合計数、並列実行の数、および最も頻繁に使用される RevoScaleR 関数を確認できます。
  現在、レポートで監視されるのは、RevoScaleR パッケージ関数の統計のみです。
  このレポートの T-SQL コードを取得する場合は、 **[SQL スクリプトの表示]** をクリックします。 

+ **R Services - Extended Events**

  このレポートを使用して、R スクリプトの実行を監視するために使用できる拡張イベントのリストを表示します。 
  このレポートの T-SQL コードを取得する場合は、 **[SQL スクリプトの表示]** をクリックします。

+ **R Services - Packages**

  このレポートを使用して、SQL Server インスタンスにインストールされている R パッケージのリストを表示します。 現在、レポートには以下のパッケージ プロパティが含まれます。 
  + パッケージ (名前)
  + バージョン 
  + 依存
  + ライセンス
  + ビルド済み
  + lib パス

+ **R Services - Resource Usage**

  このレポートを使用して、SQL Server R スクリプトの実行ごとに CPU、メモリ、および I/O リソースの消費量を表示します。 外部のリソース プールのメモリ設定を表示することもできます。 


## <a name="see-also"></a>参照

[R Services の監視](../../advanced-analytics/r-services/monitoring-r-services.md)

[R Services の拡張イベント](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md)


