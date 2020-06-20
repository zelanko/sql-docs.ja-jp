---
title: model データベース | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- template databases [SQL Server]
- model database [SQL Server], about model databases
- model database [SQL Server]
ms.assetid: 4e4f739b-fd27-4dce-8be6-3d808040d8d7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 298723c5031299b1b105f686e188e1e27cfd758c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965879"
---
# <a name="model-database"></a>model データベース
  **model** データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに作成するすべてのデータベースのテンプレートとして使用されるデータベースです。 **tempdb** は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が起動するたびに作成されるので、 **model** データベースが常に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムに存在する必要があります。 **model** データベースの内容全体 (データベース オプションを含む) が新しいデータベースにコピーされます。 **model** の設定の一部は、スタートアップ中に新しい **tempdb** を作成するためにも使用されます。このため、 **model** データベースは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システムに常に存在する必要があります。  
  
 新しく作成したユーザー データベースでは、model データベースと同じ [復旧モデル](../backup-restore/recovery-models-sql-server.md) が使用されます。 既定値はユーザー構成可能です。 モデルの現在の復旧モデルを確認する方法については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。  
  
> [!IMPORTANT]  
>  **model** データベースをユーザー固有のテンプレート情報で変更する場合は、**model** をバックアップしておくことをお勧めします。 詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。  
  
## <a name="model-usage"></a>model データベースの使用方法  
 CREATE DATABASE ステートメントが発行されると、 **model** データベースの内容がコピーされて、データベースの最初の部分が作成されます。 その新しいデータベースの残りの部分は空のページで埋められます。  
  
 **model** データベースを変更すると、変更後に作成したすべてのデータベースにその変更が継承されます。 たとえば、権限やデータベース オプションを設定したり、テーブル、関数、ストアド プロシージャなどのオブジェクトを追加できます。 **model** データベースのファイル プロパティは例外で、データ ファイルの初期サイズを除き、無視されます。  
  
## <a name="physical-properties-of-model"></a>model データベースの物理プロパティ  
 **model** データベースのデータ ファイルとログ ファイルの初期構成値を次の表に示します。 これらのファイルのサイズは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエディションによって多少異なる場合があります。  
  
|ファイル|論理名|物理名|ファイル拡張|  
|----------|------------------|-------------------|-----------------|  
|プライマリ データ|modeldev|model.mdf|ディスクがいっぱいになるまで 10% ずつ自動拡張|  
|ログ|modellog|modellog.ldf|最大 2 TB まで 10% ずつ自動拡張|  
  
 **model** データベースまたはログ ファイルを移動するには、「 [システム データベースの移動](system-databases.md)」を参照してください。  
  
### <a name="database-options"></a>データベース オプション  
 **model** データベースの各データベース オプションの既定値とそのオプションを変更できるかどうかを次の表に示します。 これらのオプションの現在の設定を表示するには、 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) カタログ ビューを使用します。  
  
|データベース オプション|既定値|変更可否|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Yes|  
|ANSI_NULL_DEFAULT|OFF|Yes|  
|ANSI_NULLS|OFF|Yes|  
|ANSI_PADDING|OFF|Yes|  
|ANSI_WARNINGS|OFF|Yes|  
|ARITHABORT|OFF|Yes|  
|AUTO_CLOSE|OFF|Yes|  
|AUTO_CREATE_STATISTICS|ON|はい|  
|AUTO_SHRINK|OFF|Yes|  
|AUTO_UPDATE_STATISTICS|ON|はい|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Yes|  
|CHANGE_TRACKING|OFF|いいえ|  
|CONCAT_NULL_YIELDS_NULL|OFF|Yes|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Yes|  
|CURSOR_DEFAULT|GLOBAL|Yes|  
|データベース可用性オプション|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|いいえ<br /><br /> [はい]<br /><br /> はい|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Yes|  
|DB_CHAINING|OFF|いいえ|  
|ENCRYPTION|OFF|いいえ|  
|NUMERIC_ROUNDABORT|OFF|Yes|  
|PAGE_VERIFY|CHECKSUM|Yes|  
|PARAMETERIZATION|SIMPLE|はい|  
|QUOTED_IDENTIFIER|OFF|はい|  
|READ_COMMITTED_SNAPSHOT|OFF|Yes|  
|RECOVERY|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エディション<sup>1</sup>に依存|Yes|  
|RECURSIVE_TRIGGERS|OFF|はい|  
|Service Broker のオプション|DISABLE_BROKER|No|  
|TRUSTWORTHY|OFF|いいえ|  
  
 <sup>1</sup>データベースの現在の復旧モデルを確認するには、「[データベースの復旧モデルを表示または変更](../backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)する」を参照してください &#40;SQL Server&#41;または[&#41;&#40;transact-sql ](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)。  
  
 これらのデータベース オプションの説明は、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。  
  
## <a name="restrictions"></a>制約  
 **model** データベースでは、次の操作を実行できません。  
  
-   ファイルまたはファイル グループの追加。  
  
-   照合順序の変更。 既定の照合順序はサーバーの照合順序です。  
  
-   データベース所有者の変更。 **model** は **sa**が所有します。  
  
-   データベースの削除。  
  
-   データベースから**guest**ユーザーを削除しています。  
  
-   変更データ キャプチャの有効化。  
  
-   データベース ミラーリングへの参加。  
  
-   プライマリ ファイル グループ、プライマリ データ ファイル、またはログ ファイルの削除。  
  
-   データベース名またはプライマリ ファイル グループ名の変更。  
  
-   データベースの OFFLINE への設定。  
  
-   プライマリ ファイル グループの READ_ONLY への設定。  
  
-   WITH ENCRYPTION オプションを使用したプロシージャ、ビュー、またはトリガーの作成。 暗号化キーは、オブジェクトが作成されたデータベースに関連付けられています。 **model** データベースで作成された暗号化オブジェクトは、 **model**データベースのみで使用できます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [システムデータベース](system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)  
  
 [データベース ファイルの移動](move-database-files.md)  
  
  
