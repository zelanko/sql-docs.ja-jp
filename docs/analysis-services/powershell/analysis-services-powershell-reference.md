---
title: "Analysis Services PowerShell リファレンス | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6c435e40-bfaf-4073-8cef-bc3260602246
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Analysis Services PowerShell リファレンス
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、Windows PowerShell を使用した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの移動、管理、およびクエリを実行するための PowerShell プロバイダー (SQLAS) とコマンドレット (SQLASCMDLETS) が含まれています。 プロバイダーとコマンドレットの読み込みと使用の詳細については、「 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)」を参照してください。 PowerShell で AMO タイプを利用して表形式データベースを作成する方法については、「 [AMO PowerShell Example](../../analysis-services/powershell/amo-powershell-example.md)」をご覧ください。  
  
##  <a name="bkmk_cmdlets"></a> Analysis Services コマンドレット  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、**Microsoft.AnalysisServices** 名前空間のメソッドに対応するコマンドレットが用意されています。 次の表は、各コマンドレットについて説明し、対応する AMO メソッドへのリンクを提供します。  
  
 PowerShell を使用して次の一覧にないタスク (たとえば、データベースの作成や同期) を実行する場合は、その操作を行うための TMSL または XMLA スクリプトを記述し、**Invoke-ASCmd** コマンドレットを使用して実行できます。  
  
|コマンドレット|Description|同等の AMO メソッド|  
|------------|-----------------|----------------------------|  
|[Add-RoleMember コマンドレット](../../analysis-services/powershell/add-rolemember-cmdlet.md)|データベース ロールにメンバーを追加します。|[<xref:Microsoft.AnalysisServices.RoleMemberCollection.Add%2A>|  
|[Backup-ASDatabase コマンドレット](../../analysis-services/powershell/backup-asdatabase-cmdlet.md)|Analysis Services データベースをバックアップします。|<xref:Microsoft.AnalysisServices.Database.Backup%2A>|  
|[Invoke-ASCmd コマンドレット](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)|XMLA または TSML (JSON) 形式のクエリまたはスクリプトを実行します。|<xref:Microsoft.AnalysisServices.Server.Execute%2A>|  
|[Invoke-ProcessASDatabase](../../analysis-services/powershell/invoke-processasdatabase.md)|データベースを処理します。|[<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessCube コマンドレット](../../analysis-services/powershell/invoke-processcube-cmdlet.md)|キューブを処理します。|[<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessDimension コマンドレット](../../analysis-services/powershell/invoke-processdimension-cmdlet.md)|ディメンションを処理します。|[<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessPartition コマンドレット](../../analysis-services/powershell/invoke-processpartition-cmdlet.md)|パーティションを処理します。|[<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Invoke-ProcessTable コマンドレット](../../analysis-services/powershell/invoke-processtable-cmdlet.md)|互換性モデル 1200 以上の表形式モデルのテーブルを処理します。|[<xref:Microsoft.AnalysisServices.IProcessable.Process%2A>|  
|[Merge-Partition コマンドレット](../../analysis-services/powershell/merge-partition-cmdlet.md)|パーティションをマージします。|<xref:Microsoft.AnalysisServices.Partition.Merge%2A>|  
|[New-RestoreFolder コマンドレット](../../analysis-services/powershell/new-restorefolder-cmdlet.md)|データベースのバックアップを格納するフォルダーを作成します|<xref:Microsoft.AnalysisServices.RestoreFolder>|  
|[New-RestoreLocation コマンドレット](../../analysis-services/powershell/new-restorelocation-cmdlet.md)|データベースの復元先となる 1 つ以上のリモート サーバーを指定します|<xref:Microsoft.AnalysisServices.RestoreLocation>|  
|[Remove-RoleMember コマンドレット](../../analysis-services/powershell/remove-rolemember-cmdlet.md)|データベース ロールからメンバーを削除します|[<xref:Microsoft.AnalysisServices.RoleMemberCollection.Remove%2A>|  
|[Restore-ASDatabase コマンドレット](../../analysis-services/powershell/restore-asdatabase-cmdlet.md)|サーバー インスタンス上にデータベースを復元します|<xref:Microsoft.AnalysisServices.Server.Restore%2A>|  
  
## 参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [PowerShell scripting in Analysis Services](../../analysis-services/instances/powershell-scripting-in-analysis-services.md)  
  
  