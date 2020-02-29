---
title: マスターデータサービス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: db2e2fb2a174e73cfbe139c3ee15529af72e5b7b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176041"
---
# <a name="master-data-services"></a>マスター データ サービス
  
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) は、マスター データ管理のための [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ソリューションです。 マスター データ管理 (MDM) とは、メンテナンス可能な形でマスターのリストをまとめることを目標に、データの非トランザクション リストを探索および定義するために組織が必要とする作業を表します。 MDM プロジェクトには、一般に、MDM テクノロジの実装と共に内部ビジネス プロセスの評価および再構築が含まれます。 優れた MDM ソリューションをビジネスの現場に導入することで、信頼性が高く分析可能なデータを一元的に管理できるようになるため、結果として、より的確な意思決定を行うことが可能になります。

 ほとんどのビジネス ユーザーは適切なトレーニングを受けることで [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ソリューションを実装できるようになります。 また、MDS を使用して、すべてのドメインの管理が可能になります。つまり、顧客、製品、またはアカウントのリスト管理のみに限定されるソリューションではありません。 MDS の初回インストール時には、どのドメインの構造も含まれていません。必要なドメインを定義するには、そのモデルを作成します。

 マスター データ サービスのその他の機能には、階層、きめ細かいセキュリティ、トランザクション、データのバージョン管理、ビジネス ルールなどがあります。

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]には、次のコンポーネントとツールが含まれています。

-   
  [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]: [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースと Web アプリケーションを作成および構成するために使用するツールです。

-   
  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]: 管理タスク (モデルやビジネス ルールの作成など) を実行するために使用し、データを更新するためにユーザーがアクセスする Web アプリケーションです。

-   MDSModelDeploy.exe: モデル オブジェクトとデータのパッケージを作成し、他の環境に配置できるようにするツールです。

-   
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Web サービス: 開発者が [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] のカスタム ソリューションを拡張または開発するために使用できます。

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]。データを管理したり、新しいエンティティや属性を作成したりするために使用します。

 MDS リソースの概要については、 [SQL Server マスターデータサービス Portal](https://go.microsoft.com/fwlink/?LinkID=214272)を参照してください。

|||
|-|-|
|**領域ごとのコンテンツの参照**<br /> ![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[マスターデータサービスの概要](master-data-services-overview-mds.md)<br /><br /> ![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[マスターデータサービス機能とタスク](../../2014/master-data-services/master-data-services-features-and-tasks.md)<br /><br /> ![小さいファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[テクニカルリファレンス (マスターデータサービス)](technical-reference-master-data-services.md)<br /><br /> ![小ファイルフォルダーアイコン](../../2014/integration-services/media/filefolder-small.gif "小さいファイル フォルダー アイコン")[開発者ガイド (マスターデータサービス)](develop/master-data-services-developer-documentation.md)||


