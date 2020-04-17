---
title: アドベンチャーワークスサンプルデータベースのインストールと構成
description: SQL Server 管理スタジオまたは Azure SQL データベースで AdventureWorks サンプル データベースをダウンロードしてインストールするには、次の手順に従います。
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 7fa3d199450750a444f2b67ae3e4583549d449b9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484571"
---
# <a name="adventureworks-installation-and-configuration"></a>アドベンチャーワークスのインストールと構成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

アドベンチャーワークスのダウンロードリンクとインストール手順。 

## <a name="prerequisites"></a>前提条件

- [SQL サーバー](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)または[Azure SQL データベース](https://azure.microsoft.com/services/sql-database/)。 完全版のサンプルでは、SQL Server 評価版/開発者/エンタープライズ エディションを使用します。
- [SQL サーバー管理スタジオ](../ssms/download-sql-server-management-studio-ssms.md) 最良の結果を得るには、2016 年 6 月以降のリリースを使用してください。
 
## <a name="oltp-downloads"></a>OLTP ダウンロード

アドベンチャーワークスのOLTPバージョンへの直接リンクは、以下にあります。

- [アドベンチャーワークス2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [アドベンチャーワークス2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [アドベンチャーワークス2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [アドベンチャーワークス2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [アドベンチャーワークス2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>データ ウェアハウスのダウンロード

AdventureWorks のデータ ウェアハウス バージョンへの直接リンクは、以下にあります。

- [アドベンチャーワークスDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [アドベンチャーワークスDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [アドベンチャーワークスDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [アドベンチャーワークスDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [アドベンチャーワークスDW2008R2.bak](https://github.com/microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-dw.bak)

## <a name="creation-scripts"></a>作成スクリプト
以下のスクリプトを使用して、バージョンに関係なく AdventureWorks データベース全体を作成できます。 

- [アドベンチャーワークス OLTP スクリプト ジップ](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [アドベンチャーワークス DW スクリプト ジップ](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>GitHub リンク

- [SQL 2014 - 2016 のすべてのアドベンチャーワークスファイル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [SQL 2012 のすべてのアドベンチャーワークスファイル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [SQL 2008 および 2008R2 のすべてのアドベンチャーワークスファイル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>SQL サーバーにインストールする

### <a name="restore-backup"></a>バックアップの復元
SQL Server 管理スタジオを使用してデータベースのバックアップを復元するには、以下の手順に従います。 

1. SQL Server 管理スタジオを開き、ターゲットの SQL Server インスタンスに接続します。
2. **[データベース**] ノードを右クリックし、[**データベースの復元**] をクリックします。
3. [**デバイス]** を選択し、省略記号 (**.)** をクリックします。
4. [**バックアップ デバイスの選択**] ダイアログで [ 追加 **]** をクリックし、サーバのファイルシステム内のデータベース バックアップに移動して、バックアップを選択します。 **[OK]** をクリックします。
5. 必要に応じて、[**ファイル**] ウィンドウでデータ ファイルとログ ファイルのターゲットの場所を変更します。 データ ファイルとログ ファイルは、別のドライブに配置することをお勧めします。
6. **[OK]** をクリックします。 これにより、データベースの復元が開始されます。 完了すると、SQL Server インスタンスにアドベンチャーワークス データベースがインストールされます。

SQL Server データベースの復元の詳細については、「 [SSMS を使用してデータベース のバックアップを復元する](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)」を参照してください。


### <a name="attach-a-datafile"></a>データファイルを添付する
SQL Server 管理スタジオを使用してデータベースのデータ ファイルをアタッチするには、次の手順に従います。

1. SQL Server 管理スタジオを開き、ターゲットの SQL Server インスタンスに接続します。
2. **[ データベース ]** ノードを右クリックし、 [**アタッチ**] を選択します。
3. [**追加]** を選択し、 に移動します。アタッチする MDF ファイル。 
1. ファイルを選択し、 **[OK]** をクリックします。 
    1. 選択したデータベースが下部ウィンドウに表示されます。 ファイルが 「見つかりません」と表示されている場合は、ファイル名の横にある省略記号 **(..**) を選択し、パスを正しいパスに更新します。 
    1. ログ ファイル (.ldf) ではなくデータ ファイル (.mdf) のみを持っている場合は、下部ウィンドウで .ldf を強調表示し、[**削除**] を選択します。 これにより、新しいログ ファイルが作成されます。 
1. **[OK] を**選択してファイルを添付します。 ファイルがアタッチされると、SQL Server インスタンスに AdventureWorks データベースがインストールされます。  

データベース ファイルのアタッチの詳細については、「データベースの[アタッチ](../relational-databases/databases/attach-a-database.md)」を参照してください。 

## <a name="install-to-azure-sql-database"></a>Azure SQL データベースにインストールする


Azure に SQL Server がまだない場合は[、Azure ポータル](https://portal.azure.com/)に移動して新しい SQL データベースを作成します。 データベースを作成するプロセスでは、サーバーを作成します。 サーバーをメモします。 [このチュートリアル](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)では、データベースを数分で作成できます。

1. Azure ポータルに接続します。
1. ナビゲーション ウィンドウの左上にある [**リソースの作成**] を選択します。 
1. **[データベース]** を選択してから、**[SQL Database]** を選択します。 
1. 必要な情報を入力します。
1. [**ソースの選択**] フィールドで、[**サンプル (AdventureWorksLT)]** を選択して、最新の AdventureWorksLT バックアップのバックアップを復元します。
1. [**作成]** を選択して、新しい SQL データベースを作成します。 


## <a name="see-also"></a>関連項目
[SQL Server 管理スタジオのチュートリアル](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[SQL Server データベース エンジンのチュートリアル](../relational-databases/database-engine-tutorials.md)
