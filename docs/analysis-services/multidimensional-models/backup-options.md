---
title: "バックアップ オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベースのバックアップ [Analysis Services]"
  - "データベース [Analysis Services], バックアップ"
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# バックアップ オプション
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースをバックアップする方法は数多くありますが、これらすべての方法では、サーバー管理者とデータベース管理者の権限が必要です。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **[バックアップ]** ダイアログ ボックスを開き、適切なオプション構成を選択し、ダイアログ ボックスから直接バックアップを実行できます。 または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。  
  
## バックアップと同期  
 データベースが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスに存在する場合は、同期機能を使用してデータベースをローカルのインスタンスにバックアップできます。 データベースの開発ビルドは、この方法で運用環境に移行できます。 従来のファイル ベースのバックアップおよび復元機能を使用して、開発ビルドを運用環境に移行することもできますが、同期機能を使用すると、追加の機能が提供されます。 同期機能を使用すると、たとえば、開発用コンピューターと実稼動コンピューターにそれぞれ異なるセキュリティ設定を使用できます。つまり、セキュリティ設定を管理し、ロール以外のすべてのオブジェクトを同期することができます。 また、コピー元コンピューターとコピー先コンピューターで異なるこれらのオブジェクトの増分更新も、通常、同期機能で行います。 この種の増分バックアップは、バックアップおよび復元機能では利用できません。 詳細については、「[Analysis Services データベースの同期](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Analysis Services サービス アカウントには、各ファイルに指定されたバックアップ場所に対する書き込み権限が必要です。 また、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの管理者ロールを持っているか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーである必要があります。  
  
## 参照  
 [[データベースのバックアップ] ダイアログ ボックス (Analysis Services - 多次元データ)](../Topic/Backup%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Backup 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [データベースのバックアップ、復元、および同期 (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  