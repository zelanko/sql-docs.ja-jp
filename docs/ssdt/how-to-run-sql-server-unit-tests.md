---
title: SQL Server 単体テストを実行する方法 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34fe2d1e-d47b-4808-af56-8cc0fdae6518
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cd78c5bc136a72fde04ccd42a02e26c26d75531a
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094626"
---
# <a name="how-to-run-sql-server-unit-tests"></a>SQL Server 単体テストを実行する方法
SQL Server の単体テストは、さまざまなウィンドウやコマンド プロンプト ウィンドウを使用するなど、複数の方法で実行できます。  
  
> [!NOTE]  
> リモートで単体テストを実行することはできません。  
  
使用できる方法は、「[SQL Server の単体テストの実行](../ssdt/running-sql-server-unit-tests.md)」で説明されているように、インストールしたソフトウェアによって異なります。  
  
### <a name="to-run-sql-server-unit-tests-using-test-view-visual-studio-2010"></a>テスト ビューを使用して SQL Server 単体テストを実行するには (Visual Studio 2010)  
  
1.  **[テスト]** メニューの **[ウィンドウ]** をポイントし、**[テスト ビュー]** をクリックします。  
  
    **[テスト ビュー]** ウィンドウが開きます。  
  
2.  **[テスト ビュー]** ウィンドウで、実行するテストをクリックします。 Ctrl キーまたは Shift キーを使用すると、連続しないテストまたは連続したテストのブロックを指定できます。  
  
3.  以下のいずれかを実行します。  
  
    -   **[テスト ビュー]** ウィンドウの任意の場所を右クリックし、**[選択範囲の実行]** をクリックします。  
  
    -   **[テスト ビュー]** ツール バーの **[選択範囲の実行]** をクリックします。  
  
### <a name="to-run-sql-server-unit-tests-using-test-explorer-visual-studio-2012"></a>テスト エクスプローラーを使用して SQL Server 単体テストを実行するには (Visual Studio 2012)  
  
1.  **[テスト]** メニューの **[ウィンドウ]** をポイントし、**[テスト エクスプローラー]** をクリックします。  
  
    **[テスト エクスプローラー]** ウィンドウが開きます。  
  
2.  **テスト エクスプローラー**で、実行するテストをクリックします。 Ctrl キーまたは Shift キーを使用すると、連続しないテストまたは連続したテストのブロックを指定できます。  
  
3.  強調表示されたテストの 1 つを右クリックし、**[選択したテストの実行]** をクリックします。  
  
### <a name="to-run-sql-server-unit-tests-from-the-sql-server-unit-test-designer-visual-studio-2010"></a>SQL Server 単体テスト デザイナーを使用して SQL Server 単体テストを実行するには (Visual Studio 2010)  
  
-   **[テスト ツール]** ツール バーには、デバッガーを使用してプロジェクトを開始するボタンまたはデバッガーを使用しないでプロジェクトを開始するボタンがあります。  
  
この手順により、現在のテスト実行内のすべてのテストが実行されます。 テストの実行を開始するとすぐに、**[テスト結果]** ウィンドウが表示され、テスト実行の進行状況が表示されます。 この表示には、実行中のテストと完了したテストが含まれます。 詳細については、「[SQL Server の単体テストの結果の解釈](../ssdt/interpreting-sql-server-unit-test-results.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[SQL Server の単体テストの実行](../ssdt/running-sql-server-unit-tests.md)  
[方法: Microsoft Visual Studio から自動テストを実行する (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182470(VS.100).aspx)  
[コマンド ラインからの自動テストの実行 (Visual Studio 2010)](http://msdn.microsoft.com/library/ms182486(VS.100).aspx)  
[アプリケーションのテスト (Visual Studio 2012)](http://msdn.microsoft.com/library/ms182409.aspx)  
  
