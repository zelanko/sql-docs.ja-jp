---
title: model データベース | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- template databases [SQL Server]
- model database [SQL Server], about model databases
- model database [SQL Server]
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
caps.latest.revision: 52
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84b01fb62721b624ffde822f041dd160671d0840
ms.sourcegitcommit: a083e9d59e2014a06cda9138b7e17c17ecab90e0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2018
ms.locfileid: "44343111"
---
# <a name="model-database"></a>model データベース
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **model** データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに作成するすべてのデータベースのテンプレートとして使用されるデータベースです。 **tempdb** は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動するたびに作成されるので、 **model** データベースが常に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムに存在する必要があります。 **model** データベースの内容全体 (データベース オプションを含む) が新しいデータベースにコピーされます。 **model** の設定の一部は、スタートアップ中に新しい **tempdb** を作成するためにも使用されます。このため、 **model** データベースは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムに常に存在する必要があります。  
  
 新しく作成したユーザー データベースでは、model データベースと同じ [復旧モデル](../../relational-databases/backup-restore/recovery-models-sql-server.md) が使用されます。 既定値はユーザー構成可能です。 モデルの現在の復旧モデルを確認する方法については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。  
  
> [!IMPORTANT]  
>  **model** データベースをユーザー固有のテンプレート情報で変更する場合は、**model** をバックアップしておくことをお勧めします。 詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。  
  
## <a name="model-usage"></a>model データベースの使用方法  
 CREATE DATABASE ステートメントが発行されると、 **model** データベースの内容がコピーされて、データベースの最初の部分が作成されます。 その新しいデータベースの残りの部分は空のページで埋められます。  
  
 **model** データベースを変更すると、変更後に作成したすべてのデータベースにその変更が継承されます。 たとえば、権限やデータベース オプションを設定したり、テーブル、関数、ストアド プロシージャなどのオブジェクトを追加できます。 **model** データベースのファイル プロパティは例外で、データ ファイルの初期サイズを除き、無視されます。 model データベースのデータ ファイルとログ ファイルの既定の初期サイズは、8 MB です。  
  
## <a name="physical-properties-of-model"></a>model データベースの物理プロパティ  
 **model** データベースのデータ ファイルとログ ファイルの初期構成値を次の表に示します。  
  
|ファイル|論理名|物理名|ファイル拡張|  
|----------|------------------|-------------------|-----------------|  
|プライマリ データ|modeldev|model.mdf|ディスクがいっぱいになるまで 64 MB ずつ自動拡張|  
|Log|modellog|modellog.ldf|最大 2 TB まで 64 MB ずつ自動拡張|  
  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] より前のバージョンでの既定のファイル拡張値については、「[model データベース](../../2014/relational-databases/databases/model-database.md)」をご覧ください。  
  
 **model** データベースまたはログ ファイルを移動するには、「 [システム データベースの移動](../../relational-databases/databases/move-system-databases.md)」を参照してください。  
  
### <a name="database-options"></a>データベース オプション  
 **model** データベースの各データベース オプションの既定値とそのオプションを変更できるかどうかを次の表に示します。 これらのオプションの現在の設定を表示するには、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューを使用します。  
  
|データベース オプション|既定値|変更可否|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|[ユーザー アカウント制御]|  
|ANSI_NULL_DEFAULT|OFF|[ユーザー アカウント制御]|  
|ANSI_NULLS|OFF|[ユーザー アカウント制御]|  
|ANSI_PADDING|OFF|[ユーザー アカウント制御]|  
|ANSI_WARNINGS|OFF|[ユーザー アカウント制御]|  
|ARITHABORT|OFF|[ユーザー アカウント制御]|  
|AUTO_CLOSE|OFF|[ユーザー アカウント制御]|  
|AUTO_CREATE_STATISTICS|ON|[ユーザー アカウント制御]|  
|AUTO_SHRINK|OFF|[ユーザー アカウント制御]|  
|AUTO_UPDATE_STATISTICS|ON|[ユーザー アカウント制御]|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|[ユーザー アカウント制御]|  
|CHANGE_TRACKING|OFF|いいえ|  
|CONCAT_NULL_YIELDS_NULL|OFF|[ユーザー アカウント制御]|  
|CURSOR_CLOSE_ON_COMMIT|OFF|[ユーザー アカウント制御]|  
|CURSOR_DEFAULT|GLOBAL|[ユーザー アカウント制御]|  
|データベース可用性オプション|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|いいえ<br /><br /> はい<br /><br /> [ユーザー アカウント制御]|  
|DATE_CORRELATION_OPTIMIZATION|OFF|[ユーザー アカウント制御]|  
|DB_CHAINING|OFF|いいえ|  
|ENCRYPTION|OFF|いいえ|  
|MIXED_PAGE_ALLOCATION|ON|いいえ|  
|NUMERIC_ROUNDABORT|OFF|[ユーザー アカウント制御]|  
|PAGE_VERIFY|CHECKSUM|[ユーザー アカウント制御]|  
|PARAMETERIZATION|SIMPLE|[ユーザー アカウント制御]|  
|QUOTED_IDENTIFIER|OFF|[ユーザー アカウント制御]|  
|READ_COMMITTED_SNAPSHOT|OFF|[ユーザー アカウント制御]|  
|RECOVERY|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエディションによって異なる*|[ユーザー アカウント制御]|  
|RECURSIVE_TRIGGERS|OFF|[ユーザー アカウント制御]|  
|Service Broker のオプション|DISABLE_BROKER|いいえ|  
|TRUSTWORTHY|OFF|いいえ|  
  
 *データベースの現在の復旧モデルを確認する方法については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」または「[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)」を参照してください。  
  
 これらのデータベース オプションの説明は、「[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)」を参照してください。  
  
## <a name="restrictions"></a>制限  
 **model** データベースでは、次の操作を実行できません。  
  
-   ファイルまたはファイル グループの追加。  
  
-   照合順序の変更。 既定の照合順序はサーバーの照合順序です。  
  
-   データベース所有者の変更。 **model** は **sa**が所有します。  
  
-   データベースの削除。  
  
-   データベースからの **guest** ユーザーの削除。  
  
-   変更データ キャプチャの有効化。  
  
-   データベース ミラーリングへの参加。  
  
-   プライマリ ファイル グループ、プライマリ データ ファイル、またはログ ファイルの削除。  
  
-   データベース名またはプライマリ ファイル グループ名の変更。  
  
-   データベースの OFFLINE への設定。  
  
-   プライマリ ファイル グループの READ_ONLY への設定。  
  
-   WITH ENCRYPTION オプションを使用したプロシージャ、ビュー、またはトリガーの作成。 暗号化キーは、オブジェクトが作成されたデータベースに関連付けられています。 **model** データベースで作成された暗号化オブジェクトは、 **model**データベースのみで使用できます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [システム データベース](../../relational-databases/databases/system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
 [データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)  
  
  
