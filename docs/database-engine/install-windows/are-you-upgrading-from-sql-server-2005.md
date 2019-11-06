---
title: SQL Server 2005、2008、または 2008R2 からアップグレードしますか? | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 62389a315befed467497f87dd3b86c3f52171e91
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051211"
---
# <a name="are-you-upgrading-from-sql-server-2005-2008-or-2008r2"></a>SQL Server 2005、2008、または 2008R2 からアップグレードしますか?

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 SQL Server の延長サポートの終了は、新しいバージョンの SQL Server や Azure SQL Database への早めのアップグレードをお勧めする 1 つの理由です。 アップグレードすると、セキュリティとコンプライアンスを維持し、パフォーマンスを大きく改善し、データ プラットフォームのインフラストラクチャを最適化できます。  
  
 アップグレードまたは移行の計画と自動化を行うための情報、ガイダンス、ツールの詳細については、[SQL Server 2005 のサポート終了](https://www.microsoft.com/sql-server/sql-server-2005)と[SQL Server 2008 のサポート終了](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)に関するページをご覧ください。  
  
## <a name="why-upgrade"></a>アップグレードの目的  
  
> [!IMPORTANT]  
>  SQL Server 2005 の延長サポートは 2016 年 4 月 12 日で終了しました。 2016 年 4 月 12 日を過ぎても SQL Server 2005 を実行している場合、セキュリティ更新プログラムを受け取れなくなります。  

> [!IMPORTANT]  
>  SQL Server 2008 および 2008 R2 の延長サポートは 2019 年 7 月 9 日をもって終了しました。 2019 年 7 月 9 日を過ぎても SQL Server 2008 または 2008R2 を実行している場合、セキュリティ更新プログラムを受け取れなくなります。 詳細については、[SQL Server 2008 の新しいオプションのお知らせ](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support/)に関するブログ記事を参照してください。 サポートを無料で延長するには、お客様の SQL Server を Azure VM に移行してください。 詳細については、「[Azure での SQL Server 2008 および SQL Server 2008 R2 のサポート延長](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-2008-eos-extend-support)」をご覧ください。  
  
## <a name="choose-your-upgrade-option"></a>アップグレード オプションの選択  
SQL Server の古いバージョンからリレーショナル データベースをアップグレードする場合、Microsoft プラットフォームでのリレーショナル ストレージ用のオプションがあります。  
  
これらのオプションに関するより包括的な分析内容を確認するには、[PaaS と IaaS](/azure/sql-database/sql-database-paas-vs-sql-server-iaas) に関する記事をご覧ください。  
  
|リレーショナル ストレージのオプション|利点|その他の考慮すべき要素|  
|-------------------------------|--------------|-------------------------------|  
|**Azure 仮想マシンでホストされる SQL Server**<br /><br /> 次のことが必要な場合は、このオプションの使用をご検討ください。<br /><br /> ホストされる環境への移行の利点。<br /><br /> 操作環境の制御。<br /><br /> SQL Server の使い慣れた機能セット。|**SQL Server 2008 および 2008 R2 について、無料で最大 3 年間[サポートを延長](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-2008-eos-extend-support)できます。** <br /><br /> 仮想マシン イメージのライブラリからすばやく展開できます。<br /><br /> SQL Server の完全な機能セットが利用できます。<br /><br /> ハードウェアとサーバー ソフトウェアのコストを節約できます。 1 時間単位で使用した分だけ課金されます。|SQL Server とオペレーティング システム ソフトウェアの両方を管理する必要があります。<br /><br /> <br /><br /> 詳細については、「 [Azure Virtual Machines 上の SQL Server の概要](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)」を参照してください。<br /><br /> 移行について詳しくは、「 [Azure VM の SQL Server へのデータベースの移行](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/)」をご覧ください。|  
|**Azure SQL Database マネージド インスタンス (PaaS)** <br /><br /> メンテナンスが容易で低コストのソリューションをお探しなら、このオプションをご検討ください。<br /><br /> マネージド インスタンスは、Microsoft SQL Server データベース エンジンのインスタンスに似ています。データベース用の共有リソースと、インスタンスの範囲での追加機能が提供されます。 <br /><br />マネージド インスタンスでは、オンプレミスからのデータベースの移行がサポートされ、データベースの変更は発生しないか最小限に抑えられます。|同じマネージド インスタンス内での複数データベースにまたがるクエリの利点、および CLR と SQL ジョブのサポートを得られます。 <br /><br /> 99.995% の可用性が保証されます。<br /><br /> サービスのコストには、ストレージだけでなく、高可用性、修正プログラムの適用、自動バックアップが含まれます。|Azure SQL Database マネージド インスタンスとオンプレミスの SQL Server との間には、Transact-SQL (T-SQL) に関していくつかの相違点があります。 詳しくは、[Azure SQL Database マネージド インスタンスの T-SQL 情報](/azure/sql-database/sql-database-managed-instance-transact-sql-information)に関する記事をご覧ください。<br /><br /> SQL Database マネージド インスタンスについて詳しくは、[Azure SQL Database マネージド インスタンスの概要](/azure/sql-database/sql-database-managed-instance-index)および[Azure SQL Database マネージド インスタンスの機能](/azure/sql-database/sql-database-managed-instance)に関する記事をご覧ください。<br /><br /> 移行について詳しくは、[Azure SQL Database マネージド インスタンスへの SQL Server の移行](/azure/sql-database/sql-database-managed-instance-migrate)に関する記事をご覧ください。|  
|**Azure SQL Database 単一データベースまたはエラスティック プール (PaaS)** <br /><br /> メンテナンスが容易で低コストのソリューションをお探しなら、このオプションをご検討ください。<br /><br /> このオプションは、開発者の生産性および新しいソリューションの高速な市場投入が重要になる場合や、外部アクセスを提供する必要がある場合のクラウド設計アプリケーションに対して特に適しています。 <br /><br />最もよく使用される SQL Server の機能をご利用いただけますが、Azure SQL Database マネージド インスタンスの場合よりは少なくなります。 |すばやく展開でき、簡単にスケール アップできます。<br /><br /> 99.995% の可用性が保証されます。<br /><br /> 秒単位または時間単位の使用量に対してお支払いいただけます。 <br /><br /> サービスのコストには、ストレージだけでなく、高可用性の修正プログラムの適用と、自動バックアップが含まれます。|Azure SQL Database とオンプレミスの SQL Server との間には、Transact-SQL (T-SQL) に関していくつかの相違点があります。 詳しくは、「 [Azure SQL Database の Transact-SQL 情報](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/)」を参照してください。<br /><br /> また、Azure SQL Database のデータベースの最大サイズは 100 TB である一方、SQL Server の場合は 524 PB です。 詳細については、[単一データベースに対するリソース制限](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)に関するページを参照してください。<br /><br /> SQL Database の詳細については、[Azure SQL Database の概要](https://azure.microsoft.com/services/sql-database/)ページと「[Azure SQL Database のドキュメント](/azure/sql-database/sql-database-technical-overview)」を参照してください。<br /><br /> 移行の詳細については、「 [SQL Server データベースの Azure SQL Database への移行](/azure/sql-database/sql-database-single-database-migrate)」を参照してください。|  
|**オンプレミスの SQL Server**<br /><br /> トランザクション システムからデータ ウェアハウスまで、あらゆる種類のデータベース アプリケーションに対して、このオプションをご検討ください。|ハードウェアとソフトウェアの両方を管理するので、機能と拡張性の大部分を制御できます。<br /><br /> SQL Server の古いインスタンスからアップグレードする場合、これが最も類似した環境になります。|自前のハードウェアとソフトウェアを購入、維持、管理する必要があるため、必要な先行投資は最大で、管理は最も継続的なものとなります。<br /><br /> 詳細については、「[SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-rtm)」を参照してください。|  

また、特定のデータおよびアプリケーションに対して、非リレーショナル ソリューションまたは NoSQL ソリューションを検討することもできます。  
  
|非リレーショナル ソリューション|利点|  
|------------------------------|--------------|  
|**Azure Cosmos DB**<br /><br /> JSON データを使用し、かつ堅牢なクエリ処理とトランザクション データ処理の組み合わせを必要とする最新のスケーラブルなモバイル アプリケーションや Web アプリケーションには、このオプションをご検討ください。<br /><br /> 詳細については、「[Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)」を参照してください。<br /><br /> データのインポートの詳細については、[Cosmos DB にデータをインポートする方法](https://docs.microsoft.com/azure/cosmos-db/import-data/)に関するページを参照してください。|ドキュメントにはインデックスが作成されるので、使い慣れた SQL 構文を使用してクエリを実行することができます。<br /><br /> データベースはスキーマ フリーです。<br /><br /> インデックスを再構築せずに、ドキュメントにプロパティを追加できます。<br /><br /> データベース エンジンの中でも JSON および JavaScript のサポートを利用できます。<br /><br /> 地理空間データがネイティブでサポートされており、Azure Search、HDInsight、Data Factory などの他のAzure サービスと統合できます。<br /><br /> 確保されたスループット レベルで、待機時間の短い、高パフォーマンスのストレージを利用できます。|  
|**Azure のテーブル ストレージ**<br /><br /> ペタバイト級の半構造化データをコスト効率の高いソリューションで保存するには、このオプションをご検討ください。<br /><br /> 詳しくは、「 [テーブル ストレージ](https://azure.microsoft.com/services/storage/tables/)」をご覧ください。|データをオフラインにせずに、アプリとテーブル スキーマを改善できます。<br /><br /> シャーディングせずに、データセットをスケール アップできます。<br /><br /> 複数の領域間でデータをレプリケートする地理的冗長ストレージを利用できます。|  
  
## <a name="plan-your-upgrade"></a>アップグレードの計画  
  
-   ご使用の SQL Server 2005 インスタンスのアップグレードを計画する方法については、SQL Server チームからの次の一連のブログ投稿をご確認ください。 
    - SQL Server 2005 からの効率的なアップグレードの計画:[ステップ 1/3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)、[ステップ 2/3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)、[ステップ 3/3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)
- [SQL Server 2008 のサポート終了に備えましょう](https://www.microsoft.com/sql-server/sql-server-2008)。
  
-   「[SQL Server のインストール計画](../../sql-server/install/planning-a-sql-server-installation.md)」の要件と考慮事項 (「[SQL Server のインストールに必要なハードウェアおよびソフトウェア](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」を含む) をご確認ください。  
  
-   アップグレードする方法をご確認ください。  
  
    -   「[データベース エンジンのアップグレード](../../database-engine/install-windows/upgrade-database-engine.md)」記事で使用可能なアップグレード方法を確認し、計画方法とテスト方法を学習します。  
  
        > [!IMPORTANT]  
        >- SQL Server 2005 インスタンスを SQL Server 2017 サーバーにイン プレースでアップグレードすることはできません。 SQL Server 2017 のインスタンスをインストールしてから、SQL Server 2005 データベースを新規インストールに移行する必要があります。 詳しくは、トピック「[データベース エンジンのアップグレード方法の選択](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)」の新規インストール アップグレードに関するセクションをご覧ください。  
        >- SQL 2008 および SQL 2008 R2 を SQL 2017 にインプレース アップグレードできます。 詳細については、「[サポートされているバージョンとエディションのアップグレード](supported-version-and-edition-upgrades-2017.md)」をご覧ください。 


-    アップグレードまたは移行の計画と自動化を行うための情報、ガイダンス、ツールの詳細については、[SQL Server 2005 のサポート終了](https://www.microsoft.com/sql-server/sql-server-2005)と[SQL Server 2008 のサポート終了](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)に関するページをご覧ください。  
  
## <a name="get-sql-server"></a>SQL Server を入手する  
 SQL Server の評価版コピーをダウンロードするには、[SQL Server のダウンロード](https://www.microsoft.com/sql-server/sql-server-downloads) ページをご覧ください。  
  
## <a name="next-steps"></a>Next Steps  
 [SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017)   
 [SQL Server 2005 のサポート終了](https://www.microsoft.com/sql-server/sql-server-2005)   
 [SQL Server 2008 のサポート終了](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)
  
  
