---
title: ドライバーとデータ ソースについて |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dffeea3bea7e3fbfa66e534ecaa758fbc2064d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307223"
---
# <a name="about-drivers-and-data-sources"></a>ドライバーとデータ ソースについて
*ドライバーは*、ODBC 要求を処理し、データをアプリケーションに返すコンポーネントです。 必要に応じて、ドライバーは、データ ソースによって理解される形式にアプリケーションの要求を変更します。 ドライバのセットアップ プログラムを使用して、コンピュータにドライバを追加または削除する必要があります。  
  
 *データ ソース*は、ドライバーによってアクセスされるデータベースまたはファイルであり、データ ソース名 (DSN) で識別されます。 ODBC データ ソース アドミニストレータを使用して、システムのデータ ソースを追加、構成、および削除します。 使用できるデータ ソースの種類を次の表に示します。  
  
|データ ソース|説明|  
|-----------------|-----------------|  
|User|ユーザー DSN はコンピュータに対してローカルであり、現在のユーザーのみが使用できます。 これらは、HKEY_CURRENT_USERレジストリ サブツリーに登録されます。|  
|システム|システム DSN は、ユーザー専用ではなく、コンピューターに対してローカルです。 システムまたは特権を持つユーザーは、システム DSN を使用してセットアップされたデータ・ソースを使用できます。 システム DSN は、HKEY_LOCAL_MACHINEレジストリ サブツリーに登録されます。|  
|ファイル|ファイル DSN はファイル ベースのソースであり、同じドライバーがインストールされており、データベースにアクセスできるすべてのユーザーで共有できます。 これらのデータ ソースは、ユーザー専用にする必要も、コンピューターに対してローカルである必要もありません。 ファイル データ ソース名は、専用のレジストリ エントリでは識別されません。代わりに、拡張子が .dsn のファイル名で識別されます。|  
  
 ユーザーおよびシステム データ ソースは、コンピューターに対してローカルであるため、*まとめてコンピューター*データ ソースと呼ばれます。  
  
 これらのデータ ソースには、**それぞれ [ODBC データ ソース アドミニストレータ**] ダイアログ ボックスにタブがあります。 使用できるデータ ソースの詳細については、「 [データ ソース](../../odbc/reference/data-sources.md)」を参照してください。
