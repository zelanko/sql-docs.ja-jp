---
title: Analysis Services の構成-データディレクトリ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 47d4299cde4575f7443faa1546aeffdb41fe12d5
ms.sourcegitcommit: 18a7c77be31f9af92ad9d0d3ac5eecebe8eec959
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/26/2020
ms.locfileid: "83859174"
---
# <a name="analysis-services-configuration---data-directories"></a>Analysis Services の構成 - データ ディレクトリ
  次の表にある既定のディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中にユーザーが構成できます。 これらのファイルへのアクセス許可は、ローカル管理者と、セットアップ中に作成およびプロビジョニングされる SQLServerMSASUser$\<インスタンス> セキュリティ グループのメンバーに付与されます。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
  
|説明|既定のディレクトリ|推奨事項|  
|-----------------|-----------------------|---------------------|  
|データ ルート ディレクトリ|C:\Program て SQL server の msas12。 \<InstanceID> \OLAP\Data \| \ フォルダーが制限されたアクセス許可で保護されて SQL Server いることを確認します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のパフォーマンスは、多くの構成で、データ ディレクトリが配置されているストレージのパフォーマンスに依存します。 このディレクトリは、システムに割り当てられている中でパフォーマンスが最も高いストレージに配置してください。 フェールオーバー クラスターのインストールの場合は、データ ディレクトリが共有ディスク上に配置されるようにしてください。|  
|ログ ファイル ディレクトリ|C:\Program て SQL server の msas12。 \<InstanceID> \OLAP\Log \| ログファイルのディレクトリです。このディレクトリには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] フライトレコーダーログが含まれています。 フライト レコーダーの時間を増加する場合、ログ ディレクトリに十分な容量があることを確認してください。|  
|Temp ディレクトリ|C:\Program て SQL server の msas12。 \<InstanceID> \OLAP\Temp \| は、高パフォーマンスのストレージサブシステムに Temp ディレクトリを配置します。|  
|バックアップ ディレクトリ|C:\Program て SQL server の msas12。 \<InstanceID> \OLAP\Backup \| 既定のバックアップファイルのディレクトリです [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。 PowerPivot for SharePoint のインストールでは、ここは PowerPivot System サービスが PowerPivot データ ファイルをキャッシュする場所でもあります。<br /><br /> データの損失を防ぐために適切な権限を設定し、バックアップ ディレクトリに書き込むための適切な権限が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サービスのユーザー グループに付与されるようにしてください。 マップされたドライブをバックアップ ディレクトリに使用することはサポートされていません。|  
  
## <a name="notes"></a>Notes  
  
-   SharePoint ファームに配置された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、アプリケーション ファイル、データ ファイル、およびコンテンツ データベースのプロパティとサービス アプリケーション データベースのプロパティを格納します。  
  
-   既存のインストールに機能を追加する場合、前にインストールした機能の場所は変更できません。また、新しい機能のインストール場所を指定することもできません。  
  
-   既定以外のインストール ディレクトリを指定する場合は、インストール フォルダーがこの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対して一意であることを確認します。 このダイアログ ボックスのディレクトリは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の他のインスタンスのディレクトリと共有できません。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントは、別のディレクトリにインストールする必要もあります。  
  
-   次の状況では、プログラム ファイルとデータ ファイルをインストールすることができません。  
  
    -   リムーバブル ディスク ドライブ  
  
    -   圧縮を使用したファイル システム  
  
    -   システム ファイルが配置されているディレクトリ  
  
## <a name="see-also"></a>参照  
 [SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
