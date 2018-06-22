---
title: '[復元オプション] |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], restoring
- restoring databases [Analysis Services]
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dab1bfda7ce682646cd8810ffe7317e2e65f2c04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076080"
---
# <a name="restore-options"></a>[復元オプション]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する方法は数多くありますが、どの方法でもサーバー コンピューターと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの両方に対する管理者権限が必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元するには、 **で** [データベースの復元] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを開き、このダイアログ ボックスから適切なオプション構成を選択して、復元を実行します。 または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。 この場合、次のセクションの説明に従って、XMLA を使用して復元を実行します。  
  
## <a name="restoring-databases-using-xmla"></a>XMLA を使用したデータベースの復元  
 XMLA の Restore コマンドを使用すると、.abf ファイルに基づいて復元を実行することによって復元プロセスを自動化できます。 Restore コマンドには数多くのプロパティがあり、セキュリティの定義、リモート パーティションの保存場所、リレーショナル OLAP (ROLAP) オブジェクトの再配置などを指定できます。 詳細については、次を参照してください。[復元要素&#40;XMLA&#41;](../xmla/xml-elements-commands/restore-element-xmla.md)です。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
## <a name="see-also"></a>参照  
 [データベースの復元 ダイアログ ボックス&#40;Analysis Services - 多次元データ&#41;](../restore-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services データベースのバックアップと復元](backup-and-restore-of-analysis-services-databases.md)   
 [Restore 要素&#40;XMLA&#41;](../xmla/xml-elements-commands/restore-element-xmla.md)   
 [バックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  