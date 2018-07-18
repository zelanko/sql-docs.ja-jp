---
title: 例外メッセージ ボックスのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ExceptionMessageBox class, about ExceptionMessageBox class
- exception message box [SQL Server], about exception message box
- exception message box [SQL Server]
- interfaces [SQL Server]
- exceptions [SQL Server]
- messages [SQL Server], exception message box
ms.assetid: 0b1ba514-6959-4e69-bfd2-3cf3c1ac4b9c
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 21882b1f6bb6233723a0ee7b60c7c7682abd5fa7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148373"
---
# <a name="exception-message-box-programming"></a>例外メッセージ ボックスのプログラミング
  例外メッセージ ボックス プログラム インターフェイスと共にインストールされで使用されるは[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]グラフィカルなコンポーネントです。 例外メッセージ ボックスは、サポートされるマネージド アセンブリです。アプリケーションで例外メッセージ ボックスを使用することで、メッセージ エクスペリエンスを高い柔軟性で制御し、ユーザーが後で参照できるようにエラー メッセージを保存したり、メッセージのヘルプを表示できるようにすることができます。 例外メッセージ ボックスのすべてのエディションでインストールされているため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を除く[!INCLUDE[ssEW](../../includes/ssew-md.md)]、コンピューターであれば追加構成なしで使用することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント コンポーネントがインストールされています。  
  
 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 名前空間の <xref:Microsoft.SqlServer.MessageBox> クラスには、<xref:System.Windows.Forms.MessageBox> クラスなどの全機能が含まれています。 ph x="1" /&gt; はマネージド コード例外を効率よく処理できるように設計されており、<xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> の使用が考えられる作業に最適です。 例外メッセージ ボックスを使用することで、次のことが可能になります。  
  
-   カスタマイズされたボタン テキストを最大 5 個まで提供できます。 ボタンやダイアログ ボックスのサイズは、各テキストの長さに応じて自動的に変更されます。  
  
-   メッセージのタイトル、テキスト、ボタン テキスト、ヘルプ リンクがある場合は、ユーザーがこれらをクリップボードにコピーしたり、この情報を電子メール メッセージで送信できます。  
  
-   ユーザー クリックすると、階層リレーションシップ ツリー内に基になるすべての例外やエラーを表示**追加情報**します。  
  
-   同じ例外が再度発生した場合に、メッセージを表示するかどうかをユーザーが決定できます。  
  
-   例外に関連付けられたヘルプ リンクを使って、オンライン ヘルプ システムにアクセスできます。  
  
 詳細については、次を参照してください。[プログラム例外メッセージ ボックス](../../../2014/database-engine/dev-guide/program-exception-message-box.md)します。  
  
  
