---
title: '[復元オプション] |Microsoft ドキュメント'
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3e70b5e15937b8f2c035339a7d1facfa7908ac08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="restore-options"></a>[復元オプション]
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する方法は数多くありますが、どの方法でもサーバー コンピューターと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの両方に対する管理者権限が必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元するには、 **で** [データベースの復元] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを開き、このダイアログ ボックスから適切なオプション構成を選択して、復元を実行します。 または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。 この場合、次のセクションの説明に従って、XMLA を使用して復元を実行します。  
  
## <a name="restoring-databases-using-xmla"></a>XMLA を使用したデータベースの復元  
 XMLA の Restore コマンドを使用すると、.abf ファイルに基づいて復元を実行することによって復元プロセスを自動化できます。 Restore コマンドには数多くのプロパティがあり、セキュリティの定義、リモート パーティションの保存場所、リレーショナル OLAP (ROLAP) オブジェクトの再配置などを指定できます。 詳細については、「 [Restore 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)」を参照してください。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
## <a name="see-also"></a>参照  
 [[データベースの復元] ダイアログ ボックス (Analysis Services - 多次元データ)](http://msdn.microsoft.com/library/a3990d47-55e2-424e-8eac-87edc937e806)   
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [要素 & #40; を復元します。XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [バックアップ、復元、およびデータベースとその &#40; の同期XMLA と &#41; です。](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
