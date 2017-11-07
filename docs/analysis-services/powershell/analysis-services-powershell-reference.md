---
title: "Analysis Services PowerShell リファレンス |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/21/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7999198236f93a1c64ea731659017bce4efd3e55
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-powershell-reference"></a>Analysis Services PowerShell リファレンス

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]


  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]PowerShell コマンドレットに含まれる、 [SqlServer モジュール](https://www.powershellgallery.com/packages/SqlServer/21.0.17099)です。 
  
>[!NOTE] 
> Azure Analysis Services データベースの操作は、SQL Server Analysis Services と同じの SqlServer モジュールを使用します。 ただし、すべてのコマンドレットは、Azure Analysis Services のサポートされます。 詳細については、次を参照してください。 [PowerShell での Azure Analysis Services の管理](https://docs.microsoft.com/azure/analysis-services/analysis-services-powershell)です。
  
##  <a name="bkmk_cmdlets"></a> Analysis Services コマンドレット  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、 **Microsoft.AnalysisServices** 名前空間のメソッドに対応するコマンドレットが用意されています。 次の表は、各コマンドレットについて説明し、対応する AMO メソッドへのリンクを提供します。  
  
 PowerShell を使用して次の一覧にないタスク (たとえば、データベースの作成や同期) を実行する場合は、その操作を行うための TMSL または XMLA スクリプトを記述し、 **Invoke-ASCmd** コマンドレットを使用して実行できます。  
  
|コマンドレット|Description|同等の AMO メソッド|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember コマンドレット](../../analysis-services/powershell/add-rolemember-cmdlet.md)|データベース ロールにメンバーを追加します。|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Backup-ASDatabase コマンドレット](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Analysis Services データベースをバックアップします。|[Database.Backup](https://msdn.microsoft.com/library/microsoft.analysisservices.database.backup.aspx)|  
|[Invoke-ASCmd コマンドレット](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|XMLA または TSML (JSON) 形式のクエリまたはスクリプトを実行します。|<xref:Microsoft.AnalysisServices.Core.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|データベースを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessCube コマンドレット](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|キューブを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessDimension コマンドレット](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|ディメンションを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessPartition コマンドレット](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|パーティションを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessTable コマンドレット](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|テーブル モデルでの互換性モデル 1200 以上のテーブルを処理します。|<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Merge-Partition コマンドレット](../../analysis-services/powershell/merge-partition-cmdlet.md)|パーティションをマージします。|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[New-RestoreFolder コマンドレット](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|データベースのバックアップを格納するフォルダーを作成します|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[New-RestoreLocation コマンドレット](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|データベースの復元先となる 1 つ以上のリモート サーバーを指定します|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Remove-RoleMember コマンドレット](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|データベース ロールからメンバーを削除します|<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Restore-ASDatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|サーバー インスタンス上にデータベースを復元します|<xref:Microsoft.AnalysisServices.Core.Server.Restore%2A>|  
  

  
  

