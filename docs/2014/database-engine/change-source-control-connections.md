---
title: ソース管理接続の変更 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bb9453806d27f55cf081eb1196e886cecf1789c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073824"
---
# <a name="change-source-control-connections"></a>ソース管理接続の変更
  ソース管理のソリューションを初めて追加したり開いたりしたときには、ソース管理プロバイダーによって、ローカル ソリューション ディレクトリのルート フォルダーとそれに対応するサーバー フォルダーの関連付けが作成されます。  
  
 ルート フォルダー (統合ルートとも呼ばれます) は、クライアントにあります。 これは、ソリューションやプロジェクトによって参照されるすべてのファイルを下位に含むフォルダーです。 ソリューションの最新バージョン、バージョン履歴、およびステータス情報を確認するには、ソース管理サーバーにあるサーバー フォルダーを見つけます。 サーバー フォルダーは、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe ではプロジェクトと呼ばれます。  
  
 さまざまな状況で、ソリューションをサーバー フォルダーから切断してバインドを解除する必要が生じます。 たとえば、ソース管理プロバイダーが格納されているコンピューターが使用できない場合は、バックアップ コンピューターに接続してバックアップ サーバー フォルダーにソリューションを再バインドすると、作業を正常に再開できます。 また、ソース管理プロジェクトが分割されている場合は、ソリューションを新しいプロジェクト バージョンがあるサーバー フォルダーへバインドする必要が生じることがあります。  
  
 ソリューションがバインドされているサーバー フォルダーを変更するには、ソース管理プロバイダーのユーザー インターフェイスを使用します。 ソース管理ユーザー インターフェイスは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境から開くことができます。  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a>Studio 環境からソース管理ユーザー インターフェイスを開くには  
  
1.  **ファイル** メニューのをポイント**ソース管理**、クリックして**起動 Microsoft Visual SourceSafe**です。  
  
## <a name="see-also"></a>参照  
 [ソース管理の基礎](../../2014/database-engine/source-control-basics.md)   
 [ソース管理のオプションを設定します。](../../2014/database-engine/set-source-control-options.md)   
 [ソース管理からのファイルの除外](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  