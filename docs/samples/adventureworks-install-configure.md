---
title: インストールし、AdventureWorks サンプル データベースの SQL の構成 |Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99cdd6fdf5db075cc8fd46b738f468fd5d9a028d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894927"
---
# <a name="adventureworks-installation-and-configuration"></a>AdventureWorks のインストールと構成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks のダウンロード リンクとインストール手順について。 

## <a name="prerequisites"></a>前提条件

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)または[Azure SQL Database](https://azure.microsoft.com/services/sql-database/)します。 完全なバージョンのサンプルでは、SQL Server の評価、Developer、または Enterprise Edition を使用します。
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)。 最善の結果を得るには、2016 年 6 月リリース以降を使用してください。
 
## <a name="github-links"></a>Github のリンク

- [SQL 2014、2016 のすべての AdventureWorks ファイル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [SQL 2012 のすべての AdventureWorks ファイル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [SQL 2008 および 2008 r2 のすべての AdventureWorks ファイル](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="oltp-downloads"></a>OLTP をダウンロードします。

以下の AdventureWorks OLTP バージョンへの直接リンクが見つかります。

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>データ ウェアハウスのダウンロード

以下の AdventureWorks データ ウェアハウスのバージョンへの直接リンクが見つかります。

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008-dw.bak)

## <a name="creation-scripts"></a>作成スクリプト
以下のスクリプトは、バージョンに関係なく、全体の AdventureWorks データベースの作成に使用できます。 

- [AdventureWorks OLTP スクリプト Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [AdventureWorks DW スクリプト Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="install-to-sql-server"></a>SQL Server へのインストールします。

### <a name="restore-backup"></a>バックアップを復元します。
に従って、以下の手順は、SQL Server Management Studio を使用して、データベースのバックアップを復元します。 

1. SQL Server Management Studio を開き、対象の SQL Server インスタンスに接続します。
2. **データベース**ノードを右クリックし、**Restore Database** を選択します。
3. 選択**デバイス**、省略記号ボタンをクリックします ( **.** )
4. ダイアログ ボックスで**バックアップ デバイスの選択**、 をクリックして**追加**サーバーのファイル システム内のデータベースのバックアップに移動して、バックアップを選択します。 **[OK]** をクリックします。
5. 必要に応じて、データのターゲットの場所を変更し、ログ ファイルで、**ファイル**ウィンドウ。 ベスト プラクティスとしてデータを配置し、ログ ファイルを別のドライブにあるに注意してください。
6. **[OK]** をクリックします。 これにより、データベースの復元が開始されます。 完了した後、AdventureWorks データベースの SQL Server インスタンスにインストールされている必要があります。

SQL Server データベースを復元する方法の詳細については、次を参照してください。 [SSMS を使用してデータベース バックアップを復元](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)します。


### <a name="attach-a-datafile"></a>データ ファイルをアタッチします。
に従って、以下の手順は、SQL Server Management Studio を使用して、データベースのデータ ファイルをアタッチします。

1. SQL Server Management Studio を開き、対象の SQL Server インスタンスに接続します。
2. 右クリックし、**データベース**ノード、および選択**アタッチ**します。
3. 選択**追加**に移動します。MDF ファイルがアタッチします。 
1. ファイルを選択し、をクリックして**OK**します。 
    1. 選択したデータベースは、下のウィンドウで表示する必要があります。 ファイルが表示されている場合は、"not found"として省略記号を選択します ( **.** ) 更新プログラムの正しいパスへのパスとファイルの名前の横にあります。 
    1. データ ファイル (.mdf) とログ ファイル (.ldf) ではなくをしかない場合、下のウィンドウに、.ldf を強調表示して選択**削除**します。 これにより、新しいログ ファイルが作成されます。 
1. 選択**OK**ファイルを添付します。 ファイルがアタッチされた後に、AdventureWorks データベースの SQL Server インスタンスにインストールされている必要があります。  

データベース ファイルのアタッチの詳細については、次を参照してください。[データベースをアタッチする](../relational-databases/databases/attach-a-database.md)します。 

## <a name="install-to-azure-sql-database"></a>Azure SQL Database へのインストールします。


Azure で SQL Server をまだ必要はない場合に移動、 [Azure portal](https://portal.azure.com/)し、新しい SQL データベースを作成します。 途中でデータベースを作成、サーバーを作成します。 サーバーのメモしてをおきます。 参照してください[このチュートリアル](https://azure.microsoft.com/documentation/articles/sql-database-get-started/)を数分でデータベースを作成します。

1. Azure portal に接続します。
1. 選択**リソースの作成**でナビゲーション ウィンドウの左上。 
1. 選択**データベース**選び**SQL Database**します。 
1. 要求された情報を入力します。
1. **ソースの選択**フィールドを選択します**Sample (AdventureWorksLT)** AdventureWorksLT の最新のバックアップのバックアップを復元します。
1. 選択**作成**AdventureWorksLT データベースの復元されたコピーである、新しい SQL データベースを作成します。 


## <a name="see-also"></a>関連項目
[SQL Server Management Studio のチュートリアル](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[SQL Server データベース エンジンのチュートリアル](../relational-databases/database-engine-tutorials.md)
