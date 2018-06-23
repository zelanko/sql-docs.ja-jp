---
title: SQL Server 2005 からアップグレードしますか? | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d50a66a-1845-4116-8b3a-7b5a2eeb78e6
caps.latest.revision: 16
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f5095c28bb6a5d09ae7b872272e8ed4f58efc584
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083115"
---
# <a name="are-you-upgrading-from-sql-server-2005"></a>SQL Server 2005 からアップグレードしますか?
  SQL Server 2005 の延長サポートの終了は、新しいバージョンの SQL Server や Azure SQL Database への早めのアップグレードをお勧めする 1 つの理由です。 アップグレードすると、セキュリティとコンプライアンスを維持し、パフォーマンスを大きく改善し、データ プラットフォームのインフラストラクチャを最適化できます。  
  
 アップグレードまたは移行の計画と自動化を行うための情報、ガイダンス、ツールの詳細については、「 [SQL Server 2005 のサポート終了](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)」をご覧ください。  
  
## <a name="why-upgrade"></a>アップグレードの目的  
  
> [!IMPORTANT]  
>  SQL Server 2005 の延長サポートは 2016 年 4 月 12 日で終了します。 2016 年 4 月 12 日を過ぎても SQL Server 2005 を実行している場合、セキュリティ更新プログラムを受け取れなくなります。  
  
 SQL Server 2005 からのアップグレードに関する PDF 形式でデータ シートを入手する[ここをクリックして](https://info.microsoft.com/rs/157-GQE-382/images/EN-CNTNT-Infographic-UpgradeSQL2005Datasheet.pdf)(下のサムネイル画像) ではなくです。  
  
 ![SQL Server 2005 からのアップグレードに関するデータ シート](../../../2014/sql-server/install/media/sqlserver2005eos.png "SQL Server 2005 からのアップグレードに関するデータ シート")  
  
## <a name="choose-your-upgrade-option"></a>アップグレード オプションの選択  
 ここでは、リレーショナル データベースを SQL Server 2005 からアップグレードする場合に使用できる、Microsoft プラットフォームでのリレーショナル ストレージ用のオプションを示します。  
  
 これらのオプションの包括的な分析の詳細を確認するには、 [こちら](http://sql05upgrade.azurewebsites.net/)をクリックします。  
  
|リレーショナル ストレージのオプション|利点|その他の考慮すべき要素|  
|-------------------------------|--------------|-------------------------------|  
|**オンプレミスの SQL Server**<br /><br /> トランザクション システムからデータ ウェアハウスまで、あらゆる種類のデータベース アプリケーションに対して、このオプションをご検討ください。<br /><br /> 詳細については、次を参照してください。 [SQL Server 2014](https://www.microsoft.com/EN-US/server-cloud/products/sql-server/)です。|ハードウェアとソフトウェアの両方を管理するので、機能と拡張性の大部分を制御できます。<br /><br /> SQL Server 2005 からアップグレードする場合、これが最も類似した環境になります。|自前のハードウェアとソフトウェアを購入、維持、管理する必要があるため、必要な先行投資は最大で、管理は最も継続的なものとなります。|  
|**Azure 仮想マシンでホストされる SQL Server**<br /><br /> 次のことが必要な場合は、このオプションをご検討ください。<br />-ホストされた環境への移行の利点があります。<br />-この運用環境を制御します。<br />の SQL server 使い慣れた機能セット。<br /><br /> 詳細については、次を参照してください。 [Azure の仮想マシンの概要 SQL Server](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)です。<br /><br /> 移行について詳しくは、「 [Azure VM の SQL Server へのデータベースの移行](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/)」をご覧ください。|仮想マシン イメージのライブラリからすばやく展開できます。<br /><br /> SQL Server の完全な機能セットが利用できます。<br /><br /> ハードウェアとサーバー ソフトウェアのコストを節約できます。 1 時間単位で使用した分だけ課金されます。|SQL Server と、オペレーティング システム ソフトウェアの両方を構成して管理する必要があります。|  
|**Azure SQL Database のホストされるデータベース サービス**<br /><br /> メンテナンスが容易で低コストのソリューションをお探しなら、このオプションをご検討ください。<br /><br /> このオプションは、必要なキャパシティがいつも同じではないアプリ、または外部アクセスを許可する必要のあるアプリに、特に適しています。<br /><br /> 詳細については、次を参照してください。 [SQL データベース](https://azure.microsoft.com/services/sql-database/)です。<br /><br /> 移行する方法の詳細については、次を参照してください。 [Azure SQL データベースに SQL Server データベースを移行する](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/)です。|すばやく展開でき、簡単にスケール アップできます。<br /><br /> 1 時間単位で使用した分だけ課金されます。<br /><br /> サービスのコストには、ストレージだけでなく高可用性の自動バックアップが含まれています。|Azure SQL Database には、ホストされるクラウド環境には当てはまらない一部の SQL Server の機能が装備されていません。 詳しくは、「 [Azure SQL Database の Transact-SQL 情報](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/)」を参照してください。<br /><br /> また、Azure SQL Database のデータベースの最大サイズは 500 GB である一方、SQL Server は 524 PB です。|  
  
 また、特定のデータおよびアプリケーションに対して、非リレーショナル ソリューションまたは NoSQL ソリューションを検討することもできます。  
  
|非リレーショナル ソリューション|利点|  
|------------------------------|--------------|  
|**Azure DocumentDB**<br /><br /> JSON データを使用し、かつ堅牢なクエリ処理とトランザクション データ処理の組み合わせを必要とする最新のスケーラブルなモバイル アプリケーションや Web アプリケーションには、このオプションをご検討ください。<br /><br /> 詳しくは、「 [DocumentDB](https://azure.microsoft.com/en-us/services/documentdb/)」をご覧ください。|ドキュメントにはインデックスが作成されるので、使い慣れた SQL 構文を使用してクエリを実行することができます。<br /><br /> データベースはスキーマ フリーです。<br /><br /> インデックスを再構築せずに、ドキュメントにプロパティを追加できます。<br /><br /> データベース エンジンの中でも JSON および JavaScript のサポートを利用できます。<br /><br /> 地理空間データがネイティブでサポートされており、Azure Search、HDInsight、Data Factory などの他のAzure サービスと統合できます。<br /><br /> 確保されたスループット レベルで、待機時間の短い、高パフォーマンスのストレージを利用できます。|  
|**Azure のテーブル ストレージ**<br /><br /> ペタバイト級の半構造化データをコスト効率の高いソリューションで保存するには、このオプションをご検討ください。<br /><br /> 詳しくは、「 [テーブル ストレージ](https://azure.microsoft.com/services/storage/tables/)」をご覧ください。|データをオフラインにせずに、アプリとテーブル スキーマを改善できます。<br /><br /> シャーディングせずに、データセットをスケール アップできます。<br /><br /> 複数の領域間でデータをレプリケートする地理的冗長ストレージを利用できます。|  
  
 アップグレード オプションの詳細を含むレポート「SQL Server 2005 からの移行」を、Microsoft の指示によりダウンロードするには、 [こちらをクリック](https://info.microsoft.com/CO-SQL-CNTNT-FY16-09Sep-14-ModernizationDirOnMFST-Register.html) してください (下のサムネイル画像ではありません)。  
  
 ![SQL Server 2005 からの移行に関するレポート](../../../2014/sql-server/install/media/sqlserver2005migratingdoc.png "SQL Server 2005 からの移行に関するレポート")  
  
## <a name="plan-your-upgrade"></a>アップグレードの計画  
  
-   アップグレードを計画する方法については、SQL Server チームからの次の一連のブログ投稿をご確認ください。  
  
    -   [SQL Server 2005 からの効率的なアップグレードの計画: ステップ 1/3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)  
  
    -   [SQL Server 2005 からの効率的なアップグレードの計画: ステップ 2/3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)  
  
    -   [SQL Server 2005 からの効率的なアップグレードの計画: ステップ 3/3](http://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)  
  
-   要件と考慮事項を確認[SQL Server のインストール計画](../../../2014/sql-server/install/planning-a-sql-server-installation.md)など、 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)です。  
  
-   アップグレードする方法をご確認ください。  
  
    -   トピック「 [Upgrade Database Engine](../../database-engine/install-windows/upgrade-database-engine.md)」で使用可能なアップグレード方法を確認し、計画方法とテスト方法を学習します。  
  
        > [!IMPORTANT]  
        >  SQL Server 2005 サーバーを SQL Server 2014 サーバーにイン プレースでアップグレードすることはできません。 SQL Server 2014 をインストールしてから、SQL Server 2005 データベースを新規インストールに移行する必要があります。  
  
    -   詳細が記載されている「テクニカル アップグレード ガイド」を PDF 形式で入手するには、 [こちらをクリック](http://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf)してください。  
  
-   アップグレードまたは移行の計画と自動化を行うための情報、ガイダンス、ツールの詳細については、「 [SQL Server 2005 のサポート終了](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)」をご覧ください。  
  
## <a name="get-sql-server-2014"></a>SQL Server 2014 の取得  
 SQL Server 2014 の評価版をダウンロードする[ここをクリックして](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2014)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014](http://www.microsoft.com/en-us/server-cloud/products/sql-server/default.aspx)   
 [SQL Server 2005 のサポートの終了](http://www.microsoft.com/en-us/server-cloud/products/sql-server-2005/)   
 [SQL Server 2005 から SQL Server 2016 へのアップグレード](https://msdn.microsoft.com/en-US/library/mt168847.aspx)  
  
  