---
title: クラスター ディスクの選択 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ea021ed6e3613d4a39641c582e0b091ebfe1a6f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63063364"
---
# <a name="cluster-disk-selection"></a>クラスター ディスクの選択
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの共有クラスター ディスク リソースを選択するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードの **[クラスター ディスクの選択]** ページを使用します。 クラスター ディスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データが配置される場所です。  
  
 共有クラスター ディスクの要件でない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]クラスター インストールします。 SMB ファイル サーバーがサポートされているストレージを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)]フェールオーバー クラスター インストールしを使用して指定できます、**データベース エンジン - データ ディレクトリ**インストールが完了する前に ページ。  
  
> [!WARNING]  
>  Analysis Services のインストールを選択した場合は、共有クラスター ディスクを指定する必要があります。  
>   
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のフェールオーバー クラスター インスタンスで FILESTREAM を有効にする場合は、共有クラスター ディスクを指定する必要があります。  
  
## <a name="options"></a>および  
 **共有ディスク**  
 単一のディスクを一覧から選択します。 クラスター ディスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データが配置される場所です。  
  
 1 つのディスクのみを指定できます。 クラスター クォーラム リソースを含んでいるグループを選択すると、警告が表示されます。 クラスター クォーラム リソースにインストールすることはお勧めしません。  
  
 **使用可能な共有ディスク**  
 使用可能なディスクの一覧、各ディスクが共有ディスクに適しているかどうか、および各ディスク リソースの説明が表示されます。  
  
  
