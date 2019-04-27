---
title: Analysis Services PowerShell リファレンス |Microsoft Docs
ms.date: 06/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13ea15a23bbf6de6c50b494f709f65cae2f7c48b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62509841"
---
# <a name="analysis-services-powershell-reference"></a>Analysis Services PowerShell リファレンス
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] PowerShell コマンドレットに含まれる、 [SqlServer モジュール](https://www.powershellgallery.com/packages/SqlServer/21.0.17099)します。 
  
>[!NOTE] 
> Azure Analysis Services データベースの操作は、SQL Server Analysis Services と同じ SqlServer モジュールを使用します。 ただし、Azure Analysis Services のすべてのコマンドレットがサポートされています。 詳細についてを参照してください。 [PowerShell を使用した Azure Analysis Services の管理](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell)します。
  
##  <a name="bkmk_cmdlets"></a> Analysis Services コマンドレット  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、 **Microsoft.AnalysisServices** 名前空間のメソッドに対応するコマンドレットが用意されています。 次の表は、各コマンドレットについて説明し、対応する AMO メソッドへのリンクを提供します。  
  
 PowerShell を使用して次の一覧にないタスク (たとえば、データベースの作成や同期) を実行する場合は、その操作を行うための TMSL または XMLA スクリプトを記述し、 **Invoke-ASCmd** コマンドレットを使用して実行できます。  
  
|コマンドレット|説明|同等の AMO メソッド|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/Add-RoleMember)|データベース ロールにメンバーを追加します。|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Backup-ASDatabase コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/backup-asdatabase)|Analysis Services データベースをバックアップします。|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Invoke-ASCmd コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/invoke-ascmd)|XMLA または TSML (JSON) 形式のクエリまたはスクリプトを実行します。|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processasdatabase)|データベースを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessCube コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processcube)|キューブを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessDimension コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processdimension)|ディメンションを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessPartition コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processpartition)|パーティションを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessTable コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/invoke-processtable)|表形式モデル、互換性モデル 1200 以上のテーブルを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Merge-Partition コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/merge-partition)|パーティションをマージします。|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[New-RestoreFolder コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/new-restorefolder)|データベースのバックアップを格納するフォルダーを作成します|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[New-RestoreLocation コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/new-restorelocation)|データベースの復元先となる 1 つ以上のリモート サーバーを指定します|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Remove-RoleMember コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/remove-rolemember)|データベース ロールからメンバーを削除します|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Restore-ASDatabase コマンドレット](https://docs.microsoft.com/powershell/module/sqlserver/restore-asdatabase)|サーバー インスタンス上にデータベースを復元します|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  
