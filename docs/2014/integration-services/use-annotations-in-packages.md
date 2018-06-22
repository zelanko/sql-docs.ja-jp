---
title: パッケージで注釈を使用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f00ac9f1013bbf9b95999f51631970f9935364c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082793"
---
# <a name="use-annotations-in-packages"></a>パッケージで注釈を使用する
  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーには注釈の機能があります。注釈を使用すると、パッケージを自己文書化でき、パッケージを把握しやすくメンテナンスも容易になります。 注釈は、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの、制御フロー、データ フロー、およびイベント ハンドラーのデザイン画面で追加できます。 注釈には任意のデータ型のテキストを含めることができるため、パッケージにラベル、コメント、その他の説明に関する情報を追加するのに便利です。 注釈は、デザイン時のみ機能します。 たとえば、注釈をログに書き込むことはできません。  
  
 Enter キーを押すと、テキストが次の行に折り返されます。 テキスト行を追加すると、注釈ボックスのサイズが自動的に大きくなります。 パッケージ ファイルの CDATA セクションでは、パッケージの注釈はクリア テキストで残ります。  
  
 パッケージ ファイルの形式の変更の詳細については、「 [SSIS パッケージの形式](../../2014/integration-services/ssis-package-format.md)」を参照してください。  
  
 パッケージを保存すると、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーはパッケージ内に注釈を保存します。  
  
### <a name="to-add-an-annotation-to-a-package"></a>パッケージに注釈を追加するには  
  
-   [パッケージに注釈を追加する](../../2014/integration-services/add-an-annotation-to-a-package.md)  
  
  