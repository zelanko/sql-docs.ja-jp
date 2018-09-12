---
title: ソース管理接続の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], connections
ms.assetid: 538e3beb-f99c-4095-bd65-6413e872d26e
caps.latest.revision: 22
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cacfeef1468a0aec47ecd8e0b27a432bb689d1ef
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43812988"
---
# <a name="change-source-control-connections"></a>ソース管理接続の変更
  ソース管理のソリューションを初めて追加したり開いたりしたときには、ソース管理プロバイダーによって、ローカル ソリューション ディレクトリのルート フォルダーとそれに対応するサーバー フォルダーの関連付けが作成されます。  
  
 ルート フォルダー (統合ルートとも呼ばれます) は、クライアントにあります。 これは、ソリューションやプロジェクトによって参照されるすべてのファイルを下位に含むフォルダーです。 ソリューションの最新バージョン、バージョン履歴、およびステータス情報を確認するには、ソース管理サーバーにあるサーバー フォルダーを見つけます。 サーバー フォルダーは、[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe ではプロジェクトと呼ばれます。  
  
 さまざまな状況で、ソリューションをサーバー フォルダーから切断してバインドを解除する必要が生じます。 たとえば、ソース管理プロバイダーが格納されているコンピューターが使用できない場合は、バックアップ コンピューターに接続してバックアップ サーバー フォルダーにソリューションを再バインドすると、作業を正常に再開できます。 また、ソース管理プロジェクトが分割されている場合は、ソリューションを新しいプロジェクト バージョンがあるサーバー フォルダーへバインドする必要が生じることがあります。  
  
 ソリューションがバインドされているサーバー フォルダーを変更するには、ソース管理プロバイダーのユーザー インターフェイスを使用します。 ソース管理ユーザー インターフェイスは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 環境から開くことができます。  
  
#### <a name="to-open-the-source-control-user-interface-from-the-studio-environment"></a>Studio 環境からソース管理ユーザー インターフェイスを開くには  
  
1.  **ファイル**メニューで、**ソース管理**、 をクリックし、**起動 Microsoft Visual SourceSafe**します。  
  
## <a name="see-also"></a>参照  
 [ソース管理の基礎](../../2014/database-engine/source-control-basics.md)   
 [ソース管理オプションを設定します。](../../2014/database-engine/set-source-control-options.md)   
 [ソース管理からのファイルの除外](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
