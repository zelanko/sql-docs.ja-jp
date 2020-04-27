---
title: バックアップオプション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f620bafc0a734651adfe43bcf0367ca5328dc40c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66076961"
---
# <a name="backup-options"></a>バックアップ オプション
  データベースをバックアップ[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するにはさまざまな方法があり、すべての方法でサーバー管理者とデータベース管理者のアクセス許可を持っている必要があります。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] **で** [バックアップ] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを開き、適切なオプション構成を選択し、ダイアログ ボックスから直接バックアップを実行できます。 または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。  
  
## <a name="backup-and-synchronize"></a>バックアップと同期  
 データベースが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のリモート インスタンスに存在する場合は、同期機能を使用してデータベースをローカルのインスタンスにバックアップできます。 データベースの開発ビルドは、この方法で運用環境に移行できます。 従来のファイル ベースのバックアップおよび復元機能を使用して、開発ビルドを運用環境に移行することもできますが、同期機能を使用すると、追加の機能が提供されます。 同期機能を使用すると、たとえば、開発用コンピューターと実稼動コンピューターにそれぞれ異なるセキュリティ設定を使用できます。つまり、セキュリティ設定を管理し、ロール以外のすべてのオブジェクトを同期することができます。 また、コピー元コンピューターとコピー先コンピューターで異なるこれらのオブジェクトの増分更新も、通常、同期機能で行います。 この種の増分バックアップは、バックアップおよび復元機能では利用できません。 詳細については、「 [Analysis Services データベースの同期](synchronize-analysis-services-databases.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Analysis Services サービス アカウントには、各ファイルに指定されたバックアップ場所に対する書き込み権限が必要です。 また、ユーザーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの管理者ロールを持っているか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーである必要があります。  
  
## <a name="see-also"></a>参照  
 [[データベースのバックアップ] ダイアログボックス &#40;Analysis Services-多次元データ&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services データベースのバックアップと復元](backup-and-restore-of-analysis-services-databases.md)   
 [XMLA&#41;&#40;Backup 要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [データベースのバックアップ、復元、および同期 &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
