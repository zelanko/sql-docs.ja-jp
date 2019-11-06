---
title: ファイル拡張子をコード エディターに関連付ける方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- file extensions [SQL Server]
- associating file extensions [SQL Server]
- Query Editor [SQL Server Management Studio], associating file extensions
ms.assetid: 193630f4-93de-4950-8f36-68702531f925
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e67ef0d154ca1a364629545ec95416fc2d0bff19
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66064239"
---
# <a name="associate-file-extensions-to-a-code-editor"></a>ファイル拡張子をコード エディターに関連付ける方法
  ファイル拡張子を特定のコード エディターに関連付けると、Windows エクスプローラーでファイルをダブルクリックしたときに、対応する [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] コード エディターでそのファイルを開くことができます。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]でよく使用される .sql や .mdx などの拡張子は、インストール時に関連付けられます。 また、新しいファイル拡張子は、ファイル システム内で [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] に関連付ける必要があります。 この機能を使用して、他のエディターで作成されたファイルを開くことができます。また、.bak という名前に変更された .sql ファイルのバックアップなど、名前が変更されたファイルを開くことができます。  
  
 この操作には 2 つの手順があります。 まず拡張子を [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]に関連付け、次に特定のコード エディターに関連付けます。  
  
### <a name="to-associate-a-new-file-extension-with-sql-server-management-studio"></a>新しいファイル拡張子を SQL Server Management Studio に関連付けるには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[アクセサリ]** の順にポイントして、 **[エクスプローラー]** をクリックします。  
  
2.  Windows エクスプローラーで、 **[ツール]** メニューの **[フォルダー オプション]** をクリックします。  
  
3.  **[フォルダー オプション]** ダイアログ ボックスで、 **[ファイルの種類]** タブの **[新規]** をクリックします。  
  
4.  **[新しい拡張子の作成]** ダイアログ ボックスで、関連付ける新しいファイル拡張子を **[ファイルの拡張子]** ボックスに入力し、 **[OK]** をクリックします。 拡張子の先頭にピリオドを付けないでください。  
  
5.  **[登録されているファイルの種類]** ボックスで、新しい拡張子をクリックし、 **[変更]** をクリックします。  
  
6.  **[ファイルを開くプログラムの選択]** ダイアログ ボックスで **[SSMS - SQL Server Management Studio]** をクリックし、 **[OK]** をクリックします。  
  
7.  **[閉じる]** をクリックして **[フォルダー オプション]** ダイアログ ボックスを閉じ、Windows エクスプローラーを閉じます。  
  
### <a name="to-associate-a-new-file-extension-with-a-code-editor-in-sql-server-management-studio"></a>新しいファイル拡張子を SQL Server Management Studio のコード エディターに関連付けるには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **[オプション]** ダイアログ ボックスで、 **[テキスト エディター]** 、 **[ファイル拡張子]** の順にクリックします。  
  
3.  **[拡張子]** ボックスに新しいファイル拡張子を入力します。  
  
4.  **[エディター]** ボックスで、この種類のファイルを開くときに使用するコード エディターをクリックし、 **[追加]** 、 **[OK]** の順にクリックします。  
  
## <a name="see-also"></a>参照  
 [Ssms ユーティリティ](../../ssms/ssms-utility.md)  
  
  
