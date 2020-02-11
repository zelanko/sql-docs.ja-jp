---
title: データプロバイダー |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data providers [ADO]
- OLE DB providers [ADO]
- ADO, OLE DB providers
ms.assetid: 877b9f25-60c4-4ab6-8052-2c28a3849e89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40506ec971782c5e9108a34fd240faabcc2756b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925657"
---
# <a name="data-providers"></a>データ プロバイダー
データプロバイダーは、SQL データベース、インデックス付きシーケンシャルファイル、スプレッドシート、ドキュメントストア、メールファイルなど、さまざまなデータソースを表します。 プロバイダーは、行セットと呼ばれる共通の抽象化を使用して、一様にデータを公開します。  
  
 ADO は、さまざまなデータプロバイダーのいずれかに接続でき、特定のプロバイダーの特定の機能に関係なく同じプログラミングモデルを公開できるため、強力で柔軟性があります。 ただし、各データプロバイダーは一意であるため、アプリケーションと ADO の対話方法はデータプロバイダーによって異なります。  
  
 たとえば、Microsoft SQL Server データベースへのアクセスに使用される SQL Server の OLE DB プロバイダーの機能は、ファイルへのアクセスに使用される Microsoft OLE DB Provider for Internet Publishing とは大きく異なります。Web サーバーに格納されます。
