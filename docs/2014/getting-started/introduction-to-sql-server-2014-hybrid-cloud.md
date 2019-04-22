---
title: SQL Server 2014 ハイブリッド クラウドの概要 |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89344537c53c4caf066536804557451c965e4596
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59241620"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>SQL Server 2014 ハイブリッド クラウドの概要
 ほとんどのアプリケーションは、高い効率、ビジネス価値、複雑なハードウェア構成、非常に高いピーク性能の要求などの重要な課題に直面しており、業界と企業の規制に準拠する必要があります。 これらすべての要因を考慮に入れ、エンタープライズ グレードのテクノロジを構築する作業は、非常に困難になる可能性があります。 Microsoft ハイブリッド クラウド戦略は、従来型のプライベート クラウド、パブリック クラウド、およびハイブリッド クラウド環境に対して、これらの主要な課題を克服するためのサポートを提供します。 
 
 ビジネスには、オンデマンドでスケールできる柔軟な IT インフラストラクチャが必要とする場合は、データ センター内のプライベート クラウドまたは Azure のグローバル データ センターでのパブリック クラウドを構築できます。 パブリック クラウドの要件を満たすようにデータ センターを拡張する場合は、ハイブリッド クラウド モデルを構築することになります。 
 
 このトピックでは、ハイブリッド クラウド シナリオをサポートする SQL Server 2014 の機能が導入されています。 Microsoft ハイブリッド クラウド戦略と SQL Server の詳細については、「 [SQL Server ハイブリッド IT](https://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) 」Web サイトを参照してください。 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQL Server、Azure、およびハイブリッド クラウド 
 Microsoft のテクノロジを使用すると、内部設置型とクラウドの両方でコードを実行するか、内部設置型のデータを使用してクラウドで実行するか、または複数のデータ センターを活用してクラウドで全体を実行することができます。 したがって、既存の IT 投資の価値を保ったまま、独自のペースでアプリケーションをクラウドに移行することができます。 
 
 この記事で、オンプレミスの SQL Server Azure パブリック クラウドからにまたがるハイブリッド クラウドのシナリオに注目します。[Azure Virtual Machines における SQL Server](https://msdn.microsoft.com/library/azure/jj823132.aspx)と[Azure Storage](http://www.azure.com/documentation/services/storage/)します。 具体的には、次のシナリオについて説明します。 
 
-  [バックアップと復元のデータベースとの Azure Storage から](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Azure Virtual Machines 上のデータベース レプリカを管理します。](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [SQL Server データ ファイルを Azure Storage に保存します。](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [既存の SQL Server データベースを Azure 仮想マシンの移行します。](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>SQL Server と Microsoft Azure のハイブリッド クラウドのシナリオ 
 
#### <a name="backup"></a> バックアップと復元のデータベースとの Azure Storage から 
 管理者の業務のうち最も基本的なものは、データベースのバックアップと復元です。 SQL Server と Azure を使用してデータベースをクラウドで安全にバックアップできます。 
 
 バックアップ先として Azure Storage での SQL Server のバックアップと復元の機能を使用する主な利点は次のとおりです。 
 
-  容量無制限の低コスト ストレージ 
 
-  可用性の高いストレージ (地理的に分散したレプリケートによるデータ損失防止の保証) 
 
-  ディザスター リカバリーとコンプライアンスの要件をサポートできるオフサイト ストレージ 
 
-  リモート バックアップおよび復元の簡略化されたプロセス 
 
 次に、クラウドと内部設置型のシナリオで使用できる SQL Server のバックアップと復元の機能の一覧を示します。 
 
-  [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)機能では、バックアップ先として URL を指定することで Azure ストレージにバックアップすることができます。 この機能を使用すると、手動のバックアップを実行することも、ローカル ストレージまたはその他のオフサイト オプションを活用する場合と同じように独自のバックアップ方法を構成することもできます。 
 
-  [バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)機能では、保存先ストレージ、バックアップの作成中にデータを暗号化することができます。 オンプレミスと Azure Storage。 
 
-  [バックアップの圧縮 (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md)機能では、同じデータの圧縮されていないバックアップよりも小さい方のバックアップを作成することができます。 バックアップを圧縮すると、必要とされるデバイス I/O が少なくなるため、通常はバックアップ速度が大幅に向上します。 Azure Storage にバックアップ ファイルを格納する場合は、大きなメリットをもたらしますこのことができます。 
 
-  [SQL Server Managed Backup to Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx)への SQL Server データベースを自動的にバックアップする機能を使用する[Azure Storage](http://www.azure.com/documentation/services/storage/)します。 この機能を使用すると、SQL Server を構成して、単一データベースまたは複数データベースのバックアップ方法やスケジュールを管理することも、インスタンス レベルでの既定値を設定することもできます。 
 
-  [SQL Server Backup to Azure Tool](https://www.microsoft.com/download/details.aspx?id=40740) Azure Blob Storage へのバックアップを有効になり、ローカルまたはクラウドに格納されている SQL Server のバックアップを圧縮します。 このツールにより、SQL Server 2005、2008、2008 R2、2014 などの SQL Server の複数のバージョンにまたがって、単一のクラウド バックアップ戦略を使用することができます。 
 
#### <a name="replica"></a> Azure Virtual Machines 上のデータベース レプリカを管理します。 
 データベースの安定したディザスター リカバリー ソリューションは、ビジネスの成功に不可欠です。 ほとんどの顧客は、データベース レプリカを格納するためにディザスター リカバリー サイトを構成し、追加のハードウェアを購入する必要があります。 SQL Server と Azure では、クラウド内のデータベースの 1 つ以上のレプリカを保持できます。 
 
 Azure 内のセカンダリ レプリカを維持するための主な利点は次のとおりです。 
 
-  低コストのディザスター リカバリー ソリューション 
 
-  アプリケーションの透過的なフェールオーバー 
 
-  複数のレプリカを活用した、読み取りワークロードとバックアップ作業のオフロード 
 
 Azure 内のセカンダリ レプリカを維持するには、次の手法のいずれかを使用します。 
 
-  [Azure レプリカの追加ウィザード](https://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx)ディザスター リカバリーのため、Azure の仮想マシンに、データベースの 1 つまたは複数のレプリカを配置することができます。 
 
-  AlwaysOn 可用性グループ、データベース ミラーリング、およびログ配布は、アプリケーションの高可用性の宛先を選択することができ、ディザスター リカバリーの必要がある最も一般的なテクノロジです。 詳しくは、次を参照してください。[高可用性とディザスター リカバリーを Azure Virtual Machines における SQL Server](https://msdn.microsoft.com/library/azure/jj870962.aspx)します。 
 
#### <a name="store"></a> SQL Server データ ファイルを Azure Storage に保存します。 
 Azure Storage に、オンプレミスの SQL Server データ ファイルを格納するデータベースの柔軟性と信頼性が高く、無制限のオフサイト ストレージを提供します。 使用できる SQL Server 2014 以降、 [Miceosoft Azure での SQL Server データ ファイル](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure)Azure ストレージに SQL Server データベース ファイルを格納します。 この機能により、データを移動し、オンプレミスで実行される SQL Server のコンピューティング ノードを維持しながらファイルをオンプレミス データベースから Azure Storage にログインできます。 この機能を使用する Azure Storage での無制限のストレージ容量です。 
 
 SQL Server データ ファイルの Azure Storage の主な利点は次のとおりです。 
 
-  Azure Storage での無制限の低コスト ストレージ 
 
-  履歴の読み取りワークロードをクラウドにオフロードし、内部設置型アプリケーションをサポートする用途に最適 
 
-  計算インスタンス (SQL Server のインスタンス) とデータ (SQL Server データ ファイル) を分離することにより、ディザスター リカバリーを推進 これにより、簡単に、オンプレミス環境または障害が発生した場合、Azure の仮想マシンで別の SQL Server インスタンスにデータベースをアタッチすることができます。 
 
#### <a name="migrate"></a> 既存の SQL Server データベースを Azure 仮想マシンの移行します。 
 クラウド コンピューティングによって、容量無制限の仮想化リソースを従量制で使用できるなど、企業にとっていくつかの主要な利点がもたらされ、自社独自のデータセンターを構築して管理する代わりに、一般に公開されているクラウド データ センターを活用して IT コストとハードウェア コストを削減することができます。 
 
 [Azure Virtual Machines における SQL Server](https://msdn.microsoft.com/library/azure/jj823132.aspx)最小限に抑えて、オンプレミスの既存アプリケーションを Azure に移動することができます、または、コードは変更されません。 管理者と開発者は、内部設置型で使用できるのと同じ開発ツールと管理ツールを引き続き使用できます。 
 
 通常、Azure 仮想マシンを実行している SQL Server をオンプレミスの SQL Server からデータベースを移動する方法は、これらのパスのいずれかです。 
 
-  **データベースのみの移動。** いくつかのツールと Azure Virtual Machines における SQL Server への既存のオンプレミス データベースの移動に使用できる手法があります。 ガイドラインと Azure Virtual Machines における SQL Server への移行に関する推奨事項は、次を参照してください[Azure Virtual Machines における SQL Server に移行する準備を行う](https://msdn.microsoft.com/library/dn133142.aspx)また[Azure 仮想マシンで SQL Server への移行。](https://msdn.microsoft.com/library/jj156165.aspx). 
 
   さらに、SQL Server 2014 以降で、新しいウィザードでは、 [Microsoft Azure 仮想マシンに SQL Server データベースのデプロイ](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)Azure 仮想マシンで実行されている別の SQL Server インスタンスにデータベースを配置することができます。 
 
-  **仮想マシン全体を移動するには。** SQL Server 仮想マシンを Azure に持ち込むまたはプラットフォーム イメージを使用して作成できます。 次に、既にデータを格納しているデータ ディスクをアップロードして仮想マシンにアタッチすること、または空のディスクを仮想マシンにアタッチすることができます。 SQL Server データのインスタンスで発生した Azure 仮想マシンに接続されたデータ ディスクは、データ ファイルとアプリケーション データの別の永続的なストレージを提供します。 包括的な情報と操作方法について、次を参照してください。 [Azure Virtual Machines における SQL Server の展開](https://msdn.microsoft.com/library/dn133141.aspx)します。 
 
 指定された推奨事項を確認することをお勧め (プレゼンテーション層、ビジネス層、データベース層など) のアプリケーション層を Azure Virtual Machines を移動する場合、[アプリケーション パターンと開発Azure Virtual Machines における SQL Server の戦略](https://msdn.microsoft.com/library/dn574746.aspx)記事。 この記事の目的では、ソリューション設計者および開発者の基盤を提供優れたアプリケーション アーキテクチャと設計で、Azure と Azure で新しいアプリケーションを開発する既存のアプリケーションを移行するときに従うことができます。 アプリケーション パターンごとに、この記事では内部設置型のシナリオ、それに相当するクラウド対応ソリューション、および関連する技術的な推奨事項について説明します。 さらに、アプリケーションを正しく設計できるように、この記事は、Azure 固有の開発戦略について説明します。 
 
## <a name="see-also"></a>関連項目 
 [SQL Server 2014 CTP2 製品ガイド](https://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Microsoft SQL Server ハイブリッド クラウドのブログ シリーズ](https://azure.microsoft.com/blog/microsoft-sql-server-hybrid-cloud-blog-series/)  
 [データ中心のアプリケーションを Azure への移行](https://azure.microsoft.com/blog/cloud-services-series-migrating-data-centric-applications-to-windows-azure/) 
 
 
