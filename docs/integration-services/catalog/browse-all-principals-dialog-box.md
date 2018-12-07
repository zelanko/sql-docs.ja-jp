---
title: '[すべてのプリンシパルを参照] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e764f1cfd8cca7d8504a5389475e770cf934f8f
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52396675"
---
# <a name="browse-all-principals-dialog-box"></a>[すべてのプリンシパルを参照] ダイアログ ボックス
  **[すべてのプリンシパルを参照]** ダイアログ ボックスを使用して、データベースのプリンシパルを選択し、選択したプロジェクトに対する、または選択したフォルダーに格納されたすべてのプロジェクトに対するプリンシパルの権限を変更できます。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [[すべてのプリンシパルを参照] ダイアログ ボックスを開く](#open_dialog)  
  
-   [オプションの構成](#options)  
  
##  <a name="open_dialog"></a> [すべてのプリンシパルを参照] ダイアログ ボックスを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに接続します。  
  
     SSISDB カタログをホストする [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続されます。  
  
2.  オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。  
  
3.  **[SSISDB]** ノードを展開します。  
  
4.  選択したフォルダーに格納されたすべてのプロジェクトに対するプリンシパルの権限を変更するには、フォルダーを右クリックし、**[プロパティ]** をクリックします。  
  
     選択したプロジェクトに対するプリンシパルの権限を変更するには、プロジェクトが格納されているフォルダーを展開し、プロジェクトを右クリックして、**[プロパティ]** をクリックします。  
  
5.  **[権限]** ページを選択し、 **[参照]** をクリックします。  
  
##  <a name="options"></a> オプションの構成  
 このページには、SSISDB データベースのカタログ ビュー sys.database_principals から返されたプリンシパルが表示されます。  
  
 プリンシパルを選択した状態で、 **[OK]** をクリックして、 **[すべてのプリンシパルを参照]** ダイアログ ボックスを閉じると、そのプリンシパルが親ダイアログ ボックスの **[権限]** ページにある **[ログインまたはロール]** の一覧に追加されます。 **[ログインまたはロール]** の一覧にプリンシパルを追加すると、そのプリンシパルの選択したプロジェクトに対する権限を変更できます。  
  
 **[選択列]**  
 親ダイアログ ボックスの **[権限]** ページにある **[ログインまたはロール]** の一覧にプリンシパルを追加する場合はオンにします。  
  
 **[アイコン列]**  
 プリンシパルの **[種類]** に対応したアイコンです。  
  
 **名前**  
 プリンシパルの名前です。  
  
 **型**  
 プリンシパルの種類。 一般的な種類を次に示します。  
  
-   SQL ユーザー  
  
-   Windows ユーザー  
  
-   データベース ロール  
  
  
