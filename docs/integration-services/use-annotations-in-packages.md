---
title: "パッケージで注釈を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dabeecf1a4e2715bf4ccd214ac21ff3311f27411
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="use-annotations-in-packages"></a>パッケージで注釈を使用する
  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーには注釈の機能があります。注釈を使用すると、パッケージを自己文書化でき、パッケージを把握しやすくメンテナンスも容易になります。 注釈は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの、制御フロー、データ フロー、およびイベント ハンドラーのデザイン画面で追加できます。 注釈には任意のデータ型のテキストを含めることができるため、パッケージにラベル、コメント、その他の説明に関する情報を追加するのに便利です。 注釈は、デザイン時のみ機能します。 たとえば、注釈をログに書き込むことはできません。  
  
 Enter キーを押すと、テキストが次の行に折り返されます。 テキスト行を追加すると、注釈ボックスのサイズが自動的に大きくなります。 パッケージ ファイルの CDATA セクションでは、パッケージの注釈はクリア テキストで残ります。  
  
 パッケージ ファイルの形式の変更の詳細については、「 [SSIS パッケージの形式](http://msdn.microsoft.com/library/cfe0e5dc-5be3-4222-b721-fe83665edd94)」を参照してください。  
  
 パッケージを保存すると、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーはパッケージ内に注釈を保存します。  
  
## <a name="add-an-annotation-to-a-package"></a>パッケージに注釈を追加する  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、注釈を追加するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、 **[制御フロー]**タブ、 **[データ フロー]**タブ、または **[イベント ハンドラー]** タブのデザイン画面上の任意の場所を右クリックし、 **[注釈の追加]**をクリックします。 タブのデザイン画面に、テキスト ブロックが表示されます。  
  
4.  テキストを追加します。  
  
    > [!NOTE]  
    >  テキストを追加しない場合、ブロックの外側をクリックするとテキスト ブロックは削除されます。  
  
5.  注釈内のテキストのサイズまたは書式を変更するには、注釈を右クリックし、 **[テキスト注釈のフォントの設定]**をクリックします。  
  
6.  テキスト行を追加するには、Enter キーを押します。  
  
     テキスト行を追加すると、注釈ボックスのサイズが自動的に大きくなります。  
  
7.  グループに注釈を追加するには、注釈を右クリックし、 **[グループ]**をクリックします。  
  
8.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[すべてを保存]**をクリックします。  
