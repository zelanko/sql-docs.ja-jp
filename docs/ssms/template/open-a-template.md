---
title: テンプレートを開く
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- templates [Transact-SQL], opening
- opening templates
ms.assetid: 605b0f4c-5ba1-4249-ad1c-6341df77cd7a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 419f3d4fe4d91165782e10e3dc638b8488ea05e5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001553"
---
# <a name="open-a-template"></a>テンプレートを開く
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
テンプレート エクスプローラーからテンプレートを開くことができます。  
  
## <a name="to-open-a-template-from-template-explorer"></a>テンプレート エクスプローラーからテンプレートを開くには  
テンプレート エクスプローラーからテンプレートを開くことができます。  
  
1.  テンプレート エクスプローラーを開くには、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  テンプレート カテゴリの一覧で、開こうとしているテンプレートを含むカテゴリを展開します。  
  
3.  テンプレートを開くには、次の 3 とおりの方法があります。  
  
    1.  テンプレートをダブルクリックしてコード エディター ウィンドウで開きます。  
  
    2.  テンプレートを右クリックして **[開く]** を選択し、コード エディター ウィンドウで開きます。  
  
    3.  テンプレートをコード エディター ウィンドウにドラッグし、テンプレート コードをエディター ウィンドウの内容に追加します。  
  
テンプレートを開いた後、 **[テンプレート パラメーターの値の指定]** ダイアログ ボックスでテンプレート パラメーターを適切な値に置き換えます。  
  
テンプレートを開いて新しいエディター ウィンドウが起動する場合、そのウィンドウは、現在のアクティブな接続の資格情報によって開きます。 たとえば、CREATE DATABASE テンプレートを開くときに、オブジェクト エクスプローラーで [!INCLUDE[ssDE](../../includes/ssde_md.md)] のインスタンスにフォーカスがあると、そのインスタンスへの接続を使用して新しいエディター ウィンドウが開きます。 アクティブな接続がない場合は、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] によってログイン ダイアログが表示されます。  
  
## <a name="see-also"></a>参照  
[テンプレート エクスプローラー](../../ssms/template/template-explorer.md)  
[テンプレート パラメーターの置換](../../ssms/template/replace-template-parameters.md)  
  
