---
title: 接続されているデータベース開発
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 21f7f959-7b8e-4335-8681-bebcd957692c
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 068418e04624d912671e5b390823fb0903ba50af
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75256126"
---
# <a name="connected-database-development"></a>接続されているデータベース開発

このセクションでは、接続されているデータベースのデザインおよび照会を行うために SQL Server Data Tools で提供されている機能について説明します。  
  
開発者は Visual Studio の SQL Server オブジェクト エクスプローラーを使用して、データベース オブジェクトの作成、編集、および参照をオンプレミスのデータベース サーバー (SQL Server 2008、Microsoft SQL Server 2012 など) またはオフプレミス (SQL Azure) で実行できるようになりました。 開発者は既存の運用データベースを容易に複製してテスト インスタンスを作成し、これに対して追加の開発作業を行い、変更を元の運用データベースに公開することができます。  
  
> [!NOTE]  
> このセクションの操作方法に関するトピックには、順番に完了する一連のタスクが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|[説明]|  
|---------|---------------|  
|[操作方法:データベースに接続し、既存のオブジェクトを参照する](../ssdt/how-to-connect-to-a-database-and-browse-existing-objects.md)|データベースに接続してデータベースのエンティティを参照します。|  
|[テーブル デザイナーを使用してデータベース オブジェクトを作成する方法](../ssdt/how-to-create-database-objects-using-table-designer.md)|新しいテーブル デザイナーを使用してテーブルをデザインし、テーブルのリレーションシップを管理します。|  
|[接続されているデータベースを Power Buffer で更新する方法](../ssdt/how-to-update-a-connected-database-with-power-buffer.md)|ALTER スクリプトを作成することなく、接続されているデータベースを更新します。|  
|[[フィルターと並べ替え] ダイアログ ボックス](../ssdt/filter-and-sort-dialog-box.md)|データ ビューに表示するデータを指定します。|  
|[クエリを使用して新しいデータベース オブジェクトを作成する方法](../ssdt/how-to-create-new-database-objects-using-queries.md)|Transact\-SQL エディターを使用して、Transact\-SQL スクリプトを編集し、実行します。|  
|[クエリを使用して既存のテーブルを編集する方法](../ssdt/how-to-edit-an-existing-table-using-queries.md)|Transact\-SQL スクリプトを作成し、テーブルの定義の編集またはデータの読み込みを行います。|  
|[テーブル内のデータを表示および編集する方法](../ssdt/how-to-view-and-edit-data-in-a-table.md)|データ エディターを使用してテーブル内のデータを表示または入力します。|  
|[オブジェクトを削除し、依存関係を解決する方法](../ssdt/how-to-delete-objects-and-resolve-dependencies.md)|データベース エンティティの名前変更または削除を行い、SQL Server Data Tools で自動的にオブジェクトの依存関係を解決します。|  
|[既存のデータベースを複製する方法](../ssdt/how-to-clone-an-existing-database.md)|運用データベースから開発用データベースを作成します。|  
|[.dacpac ファイルの抽出、発行、および登録](../ssdt/extract-publish-and-register-dacpac-files.md)|.dacpac ファイルを抽出および公開する方法について説明します。|  
  
## <a name="related-sections"></a>関連項目

[テーブルとリレーションシップの管理およびエラーの修正](../ssdt/manage-tables-relationships-and-fix-errors.md)