---
title: '[名前を付けて保存] | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.saveas
helpviewer_keywords:
- Save As dialog box
ms.assetid: 61347757-f5a3-481d-8b05-1fed086629b6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b8f64fb29a90f38d777d0963b9f985bb65e2e2a8
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701344"
---
# <a name="save-as"></a>[名前を付けて保存]
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
現在のアイテムのインスタンスを、指定した場所に指定したファイル形式で保存できます。 **ファイル** *<file>* **別名** **を保存** ( *<file>* は現在のアイテムの名前) をクリックするか、コード エディターで Alt キーを押しながら F キー、A キーの順に押します。  
  
## <a name="central-panel"></a>中央のパネル  
**[保存先]**  
このドロップダウン メニューから、既存のプロジェクト フォルダーを探します。 この一覧でフォルダーを選択すると、そのフォルダーの内容が下の主要ペインに表示されます。  
  
**[ファイル名]**  
このオプションを使用して、現在のファイル名の表示、ファイル名の変更、表示されるファイルとフォルダーのフィルター選択を行います。 表示されるファイルとフォルダーをフィルター選択するには、フィルターの対象となるファイル名またはファイル名の一部を入力します。 ワイルドカードとしてアスタリスク (`*`) を使用できます。  
  
> [!TIP]  
> Web およびネットワークの場所にあるファイルを表示するには、 **[ファイル名]** ボックスに URL またはネットワーク パスを入力します。 たとえば、「 https://mywebsite 」と入力した場合は、"mywebsite" という Web の場所で利用可能なファイルが表示され、「\\\myserver\myshare」と入力した場合は、"myserver" の "myshare" という場所で利用可能なファイルが表示されます。  
  
**ファイルの種類**  
このオプションを使用して、選択したアイテムに適用する新しいファイルの種類を選択します。 選択したアイテムに適用できるすべてのファイル タイプが表示されます。  
  
**[保存オプションの詳細設定]**  
**[保存オプションの詳細設定]** ダイアログ ボックスを開くには、 **[保存]** ボタンの右側にある小さな三角形をクリックして **[エンコード付きで保存]** をクリックします。 このダイアログ ボックスを使用して、ファイルのエンコードと行末に使用する文字を指定します。  
  
## <a name="left-panel"></a>左側のパネル  
**[デスクトップ]**  
デスクトップに置かれているファイルとフォルダーをすべて表示します。  
  
**[マイ プロジェクト]**  
**[マイ プロジェクト]** または最後に開いた場所にあるファイルとフォルダーを表示します。  
  
**[マイ コンピューター]**  
コンピューターの **[マイ コンピューター]** を表示します。  
  
## <a name="see-also"></a>参照  
[[保存オプションの詳細設定]](../../ssms/menu-help/advanced-save-options.md)  
[エンコーディングによるファイルの管理](../../ssms/solution/manage-files-with-encoding.md)  
  
