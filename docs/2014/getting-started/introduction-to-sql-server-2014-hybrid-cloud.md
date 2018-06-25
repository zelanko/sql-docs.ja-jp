---
title: SQL Server 2014 ハイブリッド クラウドの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc42752-1fcd-4ab9-8194-c3001ea342e7
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fc36b9e907a9399a47b2d4f3a743e3f83bfa7a31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070543"
---
# <a name="introduction-to-sql-server-2014-hybrid-cloud"></a>SQL Server 2014 ハイブリッド クラウドの概要
 ほとんどのアプリケーションは、高い効率、ビジネス価値、複雑なハードウェア構成、非常に高いピーク性能の要求などの重要な課題に直面しており、業界と企業の規制に準拠する必要があります。 これらすべての要因を考慮に入れ、エンタープライズ グレードのテクノロジを構築する作業は、非常に困難になる可能性があります。 Microsoft ハイブリッド クラウド戦略は、従来型のプライベート クラウド、パブリック クラウド、およびハイブリッド クラウド環境に対して、これらの主要な課題を克服するためのサポートを提供します。 
 
 ビジネスでは、要求時に拡張できる柔軟性の高い IT インフラストラクチャが必要な場合は、データ センター内のプライベート クラウドまたは Azure のグローバル データ センターにパブリック クラウドを構築できます。 パブリック クラウドの要件を満たすようにデータ センターを拡張する場合は、ハイブリッド クラウド モデルを構築することになります。 
 
 このトピックでは、ハイブリッド クラウド シナリオをサポートする SQL Server 2014 の機能について説明します。 Microsoft ハイブリッド クラウド戦略と SQL Server の詳細については、次を参照してください。 [SQL Server ハイブリッド IT](http://www.microsoft.com/sqlserver/solutions-technologies/hybrid-It.aspx) web サイトです。 
 
## <a name="sql-server-azure-and-hybrid-cloud"></a>SQL Server、Azure、およびハイブリッド クラウド 
 Microsoft のテクノロジを使用すると、内部設置型とクラウドの両方でコードを実行するか、内部設置型のデータを使用してクラウドで実行するか、または複数のデータ センターを活用してクラウドで全体を実行することができます。 したがって、既存の IT 投資の価値を保ったまま、独自のペースでアプリケーションをクラウドに移行することができます。 
 
 この記事で、内部設置型 SQL Server Azure パブリック クラウドからにまたがるハイブリッド クラウドのシナリオに注目します: [Azure 仮想マシンで SQL Server](http://msdn.microsoft.com/library/azure/jj823132.aspx)と[Azure Storage](http://www.azure.com/documentation/services/storage/)です。 具体的には、次のシナリオについて説明します。 
 
-  [バックアップと復元のデータベースに/Azure ストレージから](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#backup) 
 
-  [Azure の仮想マシン上のデータベース レプリカを管理します。](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#replica) 
 
-  [Azure ストレージに SQL Server データ ファイルを保存します。](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#store) 
 
-  [既存の SQL Server データベースを Azure 仮想マシンの移行します。](../../2014/getting-started/introduction-to-sql-server-2014-hybrid-cloud.md#migrate) 
 
### <a name="hybrid-cloud-scenarios-for-sql-server-and-microsoft-azure"></a>SQL Server および Microsoft Azure のハイブリッド クラウドのシナリオ 
 
#### <a name="backup"></a> バックアップと復元のデータベースに/Azure ストレージから 
 管理者の業務のうち最も基本的なものは、データベースのバックアップと復元です。 SQL Server と Azure では、安全に、クラウド内にあるデータベースをバックアップすることができます。 
 
 Azure ストレージと SQL Server のバックアップと復元の機能を使用して、バックアップ先としての主な利点は次のとおりです。 
 
-  容量無制限の低コスト ストレージ 
 
-  可用性の高いストレージ (地理的に分散したレプリケートによるデータ損失防止の保証) 
 
-  ディザスター リカバリーとコンプライアンスの要件をサポートできるオフサイト ストレージ 
 
-  リモート バックアップおよび復元の簡略化されたプロセス 
 
 次に、クラウドと内部設置型のシナリオで使用できる SQL Server のバックアップと復元の機能の一覧を示します。 
 
-  [SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)機能では、バックアップ先として URL を指定することによって Azure ストレージにバックアップすることができます。 この機能を使用すると、手動のバックアップを実行することも、ローカル ストレージまたはその他のオフサイト オプションを活用する場合と同じように独自のバックアップ方法を構成することもできます。 
 
-  [バックアップの暗号化](../relational-databases/backup-restore/backup-encryption.md)機能では、バックアップ先ストレージを作成するときにデータを暗号化することができます。 オンプレミスと Azure Storage。 
 
-  [バックアップの圧縮 (SQL Server)](../relational-databases/backup-restore/backup-compression-sql-server.md)機能では、これは、同じデータの圧縮されていないバックアップよりも小さいバックアップを作成することができます。 バックアップを圧縮すると、必要とされるデバイス I/O が少なくなるため、通常はバックアップ速度が大幅に向上します。 Azure ストレージにバックアップ ファイルを格納する場合は、大きなメリットをもたらしますこのことができます。 
 
-  [SQL Server Managed Backup to Azure](https://msdn.microsoft.com/library/dn606152(v=sql.120).aspx)に SQL Server データベースを自動的にバックアップする機能を使用する[Azure Storage](http://www.azure.com/documentation/services/storage/)です。 この機能を使用すると、SQL Server を構成して、単一データベースまたは複数データベースのバックアップ方法やスケジュールを管理することも、インスタンス レベルでの既定値を設定することもできます。 
 
-  [SQL Server Backup to Azure Tool](http://www.microsoft.com/download/details.aspx?id=40740) Azure Blob ストレージにバックアップを有効になり、ローカルまたはクラウドに格納されている SQL Server のバックアップを圧縮します。 このツールにより、SQL Server 2005、2008、2008 R2、2014 などの SQL Server の複数のバージョンにまたがって、単一のクラウド バックアップ戦略を使用することができます。 
 
#### <a name="replica"></a> Azure の仮想マシン上のデータベース レプリカを管理します。 
 データベースに対して安定性の高いディザスター リカバリー ソリューションを用意することは、ビジネスの成功にとって不可欠です。 ほとんどの顧客は、データベース レプリカを格納するためにディザスター リカバリー サイトを構成し、追加のハードウェアを購入する必要があります。 SQL Server と Azure では、クラウド内にあるデータベースの 1 つまたは複数のレプリカを管理できます。 
 
 Azure でセカンダリ レプリカを維持するための主な利点は次のとおりです。 
 
-  低コストのディザスター リカバリー ソリューション 
 
-  アプリケーションの透過的なフェールオーバー 
 
-  複数のレプリカを活用した、読み取りワークロードとバックアップ作業のオフロード 
 
 Azure でセカンダリ レプリカは、次の手法のいずれかを使用して管理できます。 
 
-  [Azure のレプリカの追加ウィザード](http://msdn.microsoft.com/library/dn463980\(v=sql.120\).aspx)災害復旧のため、Azure の仮想マシンに、データベースの 1 つまたは複数のレプリカを配置することができます。 
 
-  AlwaysOn 可用性グループ、データベース ミラーリング、およびログ配布は、アプリケーションの高可用性とディザスター リカバリーのニーズを満たすために使用できる非常に一般的な方法です。 詳細については、次を参照してください。[高可用性と Azure 仮想マシンで SQL Server の災害復旧](http://msdn.microsoft.com/library/azure/jj870962.aspx)です。 
 
#### <a name="store"></a> Azure ストレージに SQL Server データ ファイルを保存します。 
 内部設置型 SQL Server データ ファイルを Azure ストレージに格納する、データベースの柔軟な信頼性、および容量無制限のオフサイト記憶域を提供します。 SQL Server 2014 以降を使えば[Miceosoft Azure で SQL Server データ ファイル](https://docs.microsoft.com/sql/relational-databases/databases/sql-server-data-files-in-microsoft-azure)Azure ストレージに SQL Server データベース ファイルを格納します。 この機能では、データを移動し、ログ ファイル内部設置型データベースからを Azure ストレージにオンプレミスで実行して SQL Server のコンピューティング ノードを維持しながらできます。 この機能を有効にするためが Azure ストレージ内で無制限のストレージ容量。 
 
 SQL Server データ ファイルを Azure ストレージに格納する主な利点は次のとおりです。 
 
-  Azure ストレージ内に無制限の低コスト ストレージ 
 
-  履歴の読み取りワークロードをクラウドにオフロードし、内部設置型アプリケーションをサポートする用途に最適 
 
-  計算インスタンス (SQL Server のインスタンス) とデータ (SQL Server データ ファイル) を分離することにより、ディザスター リカバリーを推進 これにより、簡単に SQL Server の内部設置型環境、または障害が発生した場合、Azure の仮想マシンに別のインスタンスにデータベースをアタッチすることができます。 
 
#### <a name="migrate"></a> 既存の SQL Server データベースを Azure 仮想マシンの移行します。 
 クラウド コンピューティングによって、容量無制限の仮想化リソースを従量制で使用できるなど、企業にとっていくつかの主要な利点がもたらされ、自社独自のデータセンターを構築して管理する代わりに、一般に公開されているクラウド データ センターを活用して IT コストとハードウェア コストを削減することができます。 
 
 [Azure 仮想マシンで SQL Server](http://msdn.microsoft.com/library/azure/jj823132.aspx)最小限に抑えて、オンプレミスの既存アプリケーションを Azure に移動することができます、またはコードは変更されません。 管理者と開発者は、内部設置型で使用できるのと同じ開発ツールと管理ツールを引き続き使用できます。 
 
 通常、Azure 仮想マシンで実行されている SQL Server に内部設置型 SQL Server からデータベースを移動する方法は、これらのパスのいずれかです。 
 
-  **データベースのみの移動:** がいくつかのツールと手法が既存の内部設置型データベースを Azure Virtual Machines での SQL サーバーの移動に使用できます。 ガイドラインと Azure 仮想マシンで SQL Server への移行に関する推奨事項については、次を参照してください[Azure 仮想マシンで SQL Server への移行の準備](http://msdn.microsoft.com/library/dn133142.aspx)、さらに[Azure 仮想マシンで SQL Server への移行。](http://msdn.microsoft.com/library/jj156165.aspx). 
 
   さらに、SQL Server 2014 以降で、新しいウィザードでは、 [Microsoft Azure 仮想マシンに SQL Server データベースの配置](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)は Azure の仮想マシンで実行されている別の SQL Server インスタンスにデータベースを展開するための使用。 
 
-  **全体の仮想マシンの移動:** を Azure に SQL Server 仮想マシンを移行またはプラットフォーム イメージを使用して作成することができます。 次に、既にデータを格納しているデータ ディスクをアップロードして仮想マシンにアタッチすること、または空のディスクを仮想マシンにアタッチすることができます。 アタッチされたデータ ディスクと Azure Virtual Machines でデータの SQL Server インスタンスを持つデータ ファイルとアプリケーション データの別の永続的な記憶域を提供します。 包括的な情報と操作方法は、次を参照してください。 [SQL Server の展開では、Azure Virtual Machines](http://msdn.microsoft.com/library/dn133141.aspx)です。 
 
 指定された推奨事項を確認することをお勧め (プレゼンテーション層、ビジネス層、およびデータベース層) などのアプリケーション層を Azure 仮想マシンを移動する場合、[アプリケーション パターンおよび開発Azure 仮想マシンで SQL Server の戦略](http://msdn.microsoft.com/library/dn574746.aspx)資料です。 この記事の目的では、ソリューション設計者と開発者の基盤を提供優れたアプリケーションのアーキテクチャと設計では Azure と Azure で新しいアプリケーションを開発する既存のアプリケーションを移行するときに従うことができます。 アプリケーション パターンごとに、この記事では内部設置型のシナリオ、それに相当するクラウド対応ソリューション、および関連する技術的な推奨事項について説明します。 さらに、アプリケーションを正しく設計することができるように、アーティクルは、Azure 特有の開発戦略について説明します。 
 
## <a name="see-also"></a>参照 
 [SQL Server 2014 CTP2 製品ガイド](http://www.microsoft.com/download/details.aspx?id=39269)  
 [SQL Server 2014](http://www.microsoft.com/sqlserver/sql-server-2014.aspx)  
 [Microsoft SQL Server ハイブリッド クラウドのブログ シリーズ](http://blogs.msdn.com/b/azure/archive/2013/10/16/microsoft-sql-server-hybrid-cloud-blog-series.aspx)  
 [Azure へのデータ セントリックなアプリケーションを移行します。](http://msdn.microsoft.com/library/jj156154.aspx) 
 
 