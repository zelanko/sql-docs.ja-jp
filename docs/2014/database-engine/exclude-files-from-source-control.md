---
title: ソース管理からファイルを除外する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding files from source control
- source controls [SQL Server Management Studio], file exclusions
ms.assetid: 7dcb6514-db5c-49eb-8b5a-2c766ce39aa7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9fb3c5ccb4fcaad062236eec6d04f995557dc2b8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933091"
---
# <a name="exclude-files-from-source-control"></a>ソース管理からのファイルの除外
  作業中のソリューションにソース管理サービスを必要としないファイルが含まれている場合は、[**ソース管理から除外**する] コマンドを使用して、ソース管理からファイルを除外できます。 ファイルを除外すると、そのファイルは [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe データベースに残りますが、プロジェクトと共にチェックインまたはチェックアウトされなくなります。  
  
 [**ソース管理から除外**する] コマンドは、生成されたファイルに対してのみ使用してください。 生成されたファイルは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ソリューション内の別のファイルの内容に基づいて、によって完全に再作成できるファイルです。  
  
### <a name="to-exclude-a-file-from-source-control"></a>ソース管理からファイルを除外するには  
  
1.  ソリューション エクスプローラーで、除外するファイルを選択します。  
  
2.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[ **Exclude** *\<file name>* **ソース管理から**除外] をクリックします。  
  
## <a name="see-also"></a>参照  
 [ソース管理の基礎](../../2014/database-engine/source-control-basics.md)   
 [ソース管理オプションの設定](../../2014/database-engine/set-source-control-options.md)   
 [ソース管理接続の変更](../../2014/database-engine/change-source-control-connections.md)  
  
  
