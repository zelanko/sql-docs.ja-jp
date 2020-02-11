---
title: チェックインされたファイルの編集 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97d6ab997a1ece36919a49243e0f1dc3cc6f3593
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779606"
---
# <a name="edit-checked-in-files"></a>チェックインされているファイルの編集
  通常、ソース管理の対象であるファイルは、チェックアウトしてから編集する必要があります。 ただし、を構成[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]して、チェックアウトしていないファイルを変更できるようにすることができます。これを行うと、ファイルを保存するまで、変更はメモリに保持されます。 ファイルの保存時に、ファイルをソース管理からチェックアウトするよう求められます。  
  
 チームで作業している場合、ソース管理プロバイダーがローカル バージョンとサーバー バージョンの両方のチェックアウトをサポートしていない限り、チェックインされているファイルの編集は許可しないでください。 ほとんどのプロバイダーはローカル バージョンのチェックアウトをサポートしていません。 プロバイダーがローカル バージョンのチェックアウトをサポートしていない場合、チェックインされているファイルを編集するときは、ファイルをチェックインする前にメモリ内のバージョンとサーバーのバージョンを手動でマージする必要があります。 この状況では、自動マージとプロバイダーが補助するマージはサポートされていません。  
  
### <a name="to-edit-checked-in-files"></a>チェックインされているファイルを編集するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  [**オプション**] ダイアログボックスで、[**ソース**] フォルダーを展開し、[**環境**] をクリックします。  
  
3.  [**チェックインされた項目の編集を許可する**] をクリックし、[ **OK**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [チェックインの管理](../../2014/database-engine/manage-checkins.md)   
 [チェックアウトの管理](../../2014/database-engine/manage-checkouts.md)  
  
  
