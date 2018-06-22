---
title: 最新バージョンとしてのバージョンを指定 |Microsoft ドキュメント
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
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 598fc6f2d90220f85cef590600d8fcf397384f28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072586"
---
# <a name="specify-a-version-as-the-latest-version"></a>最新バージョンとしてのバージョンを指定します。
  ソース管理にファイルをチェックインすると、そのバージョンが最新バージョンになります。つまり、その最新バージョンをチェックアウト (取得) するユーザーは、その最新項目のローカル コピーを受け取ることになります。  
  
 ただし、古いバージョンの項目を最新バージョンとして指定したい状況もあります。 たとえば、ファイルをチェックアウトし、そのファイルを修正してからチェックインした後に、 その修正内容を破棄することにしたとします。 既に項目をチェックインしているので、最初のチェックアウトを元に戻すことはできません。 この場合は、最初にチェックアウトしたバージョンを最新バージョンの項目として指定できます。  
  
 最新バージョンとして指定するには、以下の方法があります。  
  
-   **バージョンのピン設定**です。 ファイルのバージョンにピンを設定しても、そのバージョンよりも新しいバージョンが削除されるわけではありません。 ピンを設定したファイルのピンを解除することもできます。 ピンを解除すると、最後にチェックインしたバージョンのファイルが最新バージョンになります。 ただし、ピンを設定したファイルをチェックアウトすることはできません。  
  
-   **指定したバージョンにロールバック**です。 あるバージョンにロールバックすると、そのバージョンよりも新しいバージョンはすべてソース管理から削除されます。 その後、残っている最新バージョンをチェックアウトできます。  
  
### <a name="to-pin-a-version"></a>バージョンにピンを設定するには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ソリューションを開きます。  
  
2.  ソリューション エクスプローラーで、最新バージョンとして指定するファイルを選択します。  
  
3.  **ファイル** メニューのをポイント**ソース管理** をクリック**ViewHistory**です。  
  
4.  **の履歴**\<ファイル > ダイアログ ボックスで、最新バージョンとして指定し、をクリックするバージョンを選択して**Pin**です。  
  
     選択したバージョンの横に、それがファイルの最新バージョンであることを示すピンの記号が表示されます。 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に別のバージョンが読み込まれている場合は、ファイルの再読み込みのための画面が表示されます。  
  
### <a name="to-roll-back-to-a-version"></a>特定のバージョンにロールバックするには  
  
1.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ソリューションを開きます。  
  
2.  ソリューション エクスプローラーで、最新バージョンとして指定する項目を選択します。  
  
3.  **ファイル** メニューのをポイント**ソース管理** をクリック**履歴**です。  
  
4.  **履歴のオプション**ダイアログ ボックスで、をクリックして**OK**を表示する、**ファイルの履歴** ダイアログ ボックス。  
  
5.  **ファイルの履歴**ボックスで、最新のバージョンとして指定し、をクリックするバージョンを選択して**ロールバック**です。  
  
     選択したバージョンよりも新しいバージョンがすべて削除されることを知らせるメッセージが表示されます。  
  
6.  をクリックして**はい**を選択したバージョンにロールバックします。  
  
## <a name="see-also"></a>参照  
 [チェックインを管理します。](../../2014/database-engine/manage-checkins.md)   
 [ファイルのチェックイン](../../2014/database-engine/check-in-files.md)  
  
  