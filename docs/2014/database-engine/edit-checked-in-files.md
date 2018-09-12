---
title: ファイルの編集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 065f8d2d32d8ad16fe955ba8e36c7e65926bec95
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808288"
---
# <a name="edit-checked-in-files"></a>チェックインされているファイルの編集
  通常、ソース管理の対象であるファイルは、チェックアウトしてから編集する必要があります。 ただし、チェックアウトしていないファイルを編集できるように、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を設定できます。チェックアウトしていないファイルを編集するとき、行った変更はファイルを保存するまでメモリに保持されます。 ファイルの保存時に、ファイルをソース管理からチェックアウトするよう求められます。  
  
 チームで作業している場合、ソース管理プロバイダーがローカル バージョンとサーバー バージョンの両方のチェックアウトをサポートしていない限り、チェックインされているファイルの編集は許可しないでください。 ほとんどのプロバイダーはローカル バージョンのチェックアウトをサポートしていません。 プロバイダーがローカル バージョンのチェックアウトをサポートしていない場合、チェックインされているファイルを編集するときは、ファイルをチェックインする前にメモリ内のバージョンとサーバーのバージョンを手動でマージする必要があります。 この状況では、自動マージとプロバイダーが補助するマージはサポートされていません。  
  
### <a name="to-edit-checked-in-files"></a>チェックインされているファイルを編集するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション** ダイアログ ボックスで、展開、**ソース管理**l フォルダー、およびクリック**環境**します。  
  
3.  をクリックして**チェックイン項目の編集を許可する**、順にクリックします**OK**します。  
  
## <a name="see-also"></a>参照  
 [チェックインを管理します。](../../2014/database-engine/manage-checkins.md)   
 [チェックアウトの管理](../../2014/database-engine/manage-checkouts.md)  
  
  
