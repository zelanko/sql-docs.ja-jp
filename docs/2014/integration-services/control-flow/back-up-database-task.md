---
title: データベースのバックアップ タスク | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0980d89cc915121414dd7d3c89be6f4d72eb715
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85433999"
---
# <a name="back-up-database-task"></a>データベースのバックアップ タスク
  データベースのバックアップ タスクは、さまざまな種類の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップを実行します。 詳しくは、「[SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)」をご覧ください。  
  
 データベースのバックアップ タスクを使用すると、パッケージは単一データベースまたは複数データベースをバックアップできます。 タスクにより単一データベースのみをバックアップする場合、バックアップ対象となるデータベース、ファイル、またはファイル グループなどのコンポーネントを選択できます。  
  
## <a name="supported-recover-models-and-backup-types"></a>サポートされている復旧モデルとバックアップの種類  
 次の表に、データベースのバックアップ タスクがサポートする復旧モデルとバックアップの種類を示します。  
  
|復旧モデル|データベース|データベースの差分|[トランザクション ログ]|ファイルまたはファイルの差分|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|シンプル|必須|省略可能|サポートされていません|サポートされていません|  
|[完全]|必須|省略可能|必須|省略可能|  
|一括ログ|必須|省略可能|必須|省略可能|  
  
 データベースのバックアップ タスクは、Transact-SQL BACKUP ステートメントをカプセル化します。 詳細については、「 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)」を参照してください。  
  
## <a name="configuration-of-the-back-up-database-task"></a>データベースのバックアップ タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[データベースのバックアップ タスク] &#40;メンテナンス プラン&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)  
  
  
