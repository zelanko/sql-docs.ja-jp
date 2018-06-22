---
title: チェックインされているファイルを編集 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fd91efe4bd802a64ced4e6f93ac65f16ed4e5a71
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071529"
---
# <a name="edit-checked-in-files"></a>チェックインされているファイルの編集
  通常、ソース管理の対象であるファイルは、チェックアウトしてから編集する必要があります。 ただし、チェックアウトしていないファイルを編集できるように、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を設定できます。チェックアウトしていないファイルを編集するとき、行った変更はファイルを保存するまでメモリに保持されます。 ファイルの保存時に、ファイルをソース管理からチェックアウトするよう求められます。  
  
 チームで作業している場合、ソース管理プロバイダーがローカル バージョンとサーバー バージョンの両方のチェックアウトをサポートしていない限り、チェックインされているファイルの編集は許可しないでください。 ほとんどのプロバイダーはローカル バージョンのチェックアウトをサポートしていません。 プロバイダーがローカル バージョンのチェックアウトをサポートしていない場合、チェックインされているファイルを編集するときは、ファイルをチェックインする前にメモリ内のバージョンとサーバーのバージョンを手動でマージする必要があります。 この状況では、自動マージとプロバイダーが補助するマージはサポートされていません。  
  
### <a name="to-edit-checked-in-files"></a>チェックインされているファイルを編集するには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション** ダイアログ ボックスで、展開、**ソース管理**l フォルダー、およびクリック**環境**です。  
  
3.  をクリックして**チェックイン項目を編集することを許可する**、順にクリック**OK**です。  
  
## <a name="see-also"></a>参照  
 [チェックインを管理します。](../../2014/database-engine/manage-checkins.md)   
 [チェックアウトの管理](../../2014/database-engine/manage-checkouts.md)  
  
  