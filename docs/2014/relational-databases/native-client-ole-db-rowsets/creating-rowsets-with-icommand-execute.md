---
title: Icommand::execute で行セットの作成 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 28bfeafa028ce88b0d8132d0fdd2e29eab85b246
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420771"
---
# <a name="creating-rowsets-with-icommandexecute"></a>ICommand::Execute を使用した行セットの作成
  使用して作成された行セットの**icommand::execute**結果の行セットに必要なプロパティ、メソッドは、コマンドのテキストを制約できます。 これは、動的コマンド テキストをサポートするコンシューマーにとって特に重要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用できない[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]多数のコマンドで生成された複数の行セットの結果をサポートするカーソル。 コンシューマーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソル サポートを必要とする行セットを要求した場合に、コマンド テキストが結果として複数行を生成すると、エラーが発生します。 詳細については、次を参照してください。[コマンドを生成する複数の行セット結果](../native-client-ole-db-commands/commands-generating-multiple-rowset-results.md)します。  
  
 スクロール可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの行セットでサポートされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カーソル。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、他のデータベース ユーザーの変更によって影響を受けるカーソルに制限が設けらます。 たとえば、一部のカーソル内の行は順序付けできません。この場合に、SQL ORDER BY 句を含むコマンドを使用して行セットを作成しようとすると、エラーが発生します。 詳細については、次を参照してください。[行セットと SQL Server カーソル](rowsets-and-sql-server-cursors.md)します。  
  
## <a name="see-also"></a>参照  
 [行セット](rowsets.md)  
  
  
