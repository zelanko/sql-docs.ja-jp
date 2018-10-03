---
title: Lock Pages in Memory オプションの有効化 (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lock Pages in Memory option
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e331169f7477bfcb4a5ae926290664da50897b38
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48184962"
---
# <a name="enable-the-lock-pages-in-memory-option-windows"></a>Lock Pages in Memory オプションの有効化 (Windows)
  この Windows ポリシーにより、プロセスを使用して物理メモリにデータを保持できるアカウントを指定し、ディスク上の仮想メモリへのデータのページングを防止します。  
  
> [!NOTE]  
>  メモリ内のページをロックすると、ディスクへのメモリのページングの際にパフォーマンスが向上する場合があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が使用するアカウントに対してこのポリシーを有効にするには、Windows グループ ポリシー ツール (gpedit.msc) を使用します。 このポリシーを変更できるのは、システム管理者だけです。  
  
### <a name="to-enable-the-lock-pages-in-memory-option"></a>lock pages in memory オプションを有効にするには  
  
1.  **[スタート]** メニューの **[ファイル名を指定して実行]** をクリックします。 **オープン**ボックスに「`gpedit.msc`します。  
  
2.  **[ローカル グループ ポリシー エディター]** コンソールで **[コンピューターの構成]** を展開し、次に **[Windows の設定]** を展開します。  
  
3.  **[セキュリティの設定]** を展開し、 **[ローカル ポリシー]** を展開します。  
  
4.  **[ユーザー権利の割り当て]** フォルダーをクリックします。  
  
     ポリシーが詳細ペインに表示されます。  
  
5.  詳細ペインで、 **[メモリ内のページのロック]** をダブルクリックします。  
  
6.  **[ローカル セキュリティの設定 - メモリ内のページのロック]** ダイアログ ボックスで、 **[ユーザーまたはグループの追加]** をクリックします。  
  
7.  **[ユーザー、サービス アカウント、またはグループの選択]** ダイアログ ボックスで、sqlservr.exe の実行権限のあるアカウントを追加します。  
  
8.  この変更を有効にするには、ログアウトして、再びログインする必要があります。  
  
## <a name="see-also"></a>参照  
 [サーバー メモリに関するサーバー構成オプション](server-memory-server-configuration-options.md)  
  
  
