---
title: データ ソース (ODBC Driver for Oracle) への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to data source [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], connecting to data sources
ms.assetid: f724a9c5-342a-4f4e-a030-ec34f7378eaf
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c12472544fd843214cab4294311889d0a84010d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32900957"
---
# <a name="connecting-to-a-data-source-odbc-driver-for-oracle"></a>データ ソース (ODBC Driver for Oracle) への接続
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ODBC アプリケーションでは、さまざまな方法で接続情報を渡すことができます。 たとえば、アプリケーションには、常にユーザーに要求する接続情報、ドライバーがあります。 または、アプリケーションは、データ ソース接続を指定する接続文字列を想定して可能性があります。 データ ソースに接続する方法は、ODBC アプリケーションによって使用される接続方法によって異なります。  
  
 データ ソースに接続する 1 つの一般的な方法はデータ ソース ダイアログ ボックスです。 場合は、ODBC アプリケーションは、ダイアログ ボックスを使用してセットアップは、そのダイアログ ボックスが表示され、適切なデータ ソース接続情報を求めます。  
  
 使用してデータ ソースに接続することも、[接続文字列](../../odbc/microsoft/connection-string-format-and-attributes.md)です。  
  
### <a name="to-connect-to-a-data-source-using-a-dialog-box"></a>ダイアログ ボックスを使用してデータ ソースに接続するには  
  
1.  データ ソース ダイアログ ボックスが表示されたら、Oracle データ ソースを選択し、ok をクリックします。 [接続] ダイアログ ボックスが表示されます。  
  
2.  接続 ダイアログ ボックスの適切な情報を入力し、ok をクリックします。  
  
 接続情報の確認は、アプリケーションは、データ ソースが含まれている情報にアクセスする ODBC Driver for Oracle を使用することができます。
