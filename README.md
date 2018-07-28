# BurpSuite
## Proxy 模块（代理模块）
### 一、简介
Proxy 代理模块作为 BurpSuite 的核心功能，拦截 HTTP/S 的代理服务器，作为一个在浏览器和目标应用程序之间的中间人，允许你拦截、查看、修改在两个方向上的原始数据流。

Burp 代理允许你通过监视和操纵应用程序传输的关键参数和其他数据来查找和探索应用程序的漏洞。通过以恶意的方式修改浏览器的请求，Burp 代理可以用来进行攻击，如：SQL 注入、cookie 欺骗、提升权限、会话劫持、目录遍历、缓冲区溢出。拦截的传输可以被修改成原始文本，也可以是包含参数或者消息头的表格，也可以十六进制形式，甚至可以操纵二进制形式的数据。在 Burp 代理可以呈现出包含 HTML 或者图像数据的响应消息。

### 二、模块说明
#### 1、Intercept
用于显示和修改 HTTP 请求和响应，通过你的浏览器和 Web 服务器之间。在 BurpProxy 的选项中，您可以配置拦截规则来确定请求是什么和响应被拦截（例如：范围内的项目、与特定文件扩展名、项目要求与参数等）。该面板还包含以下控制：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.1.png)

消息类型显示的四种格式:

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.2.png)

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.3.png)

- Change request method：对所有的请求，经过把所有相关的请求参数适当地搬迁到这个请求里来，你就可以自动地把请求的方法在 POST 和 GET 中间切换。通过发送恶意的请求使用这个选项来快速测试应用程序的极限参数是多少。
- Change body encoding：对于所有的请求，你可以在应用程序／X－WWW 格式的 URL 编码和多重表单/数据之间切换消息体的编码方式。
- Copy URL：把当前的 URL 完整地复制到粘贴板上。
- Cope to file：这个功能允许你把选择一个文件，并把消息的内容复制到这个文件里。这个对二进制数据来说是很方便的，要是通过粘贴板来复制会带来一些问题。复制操作是在选择的文本上进行的，如果没有被选中的内容，则是针对整个消息了。
- Pase form file：这个功能允许你选择一个文件，并把文件里的内容粘贴到消息里。这个对二进制数据来说是很方便的，要是通过粘贴板来复制会带来一些问题。粘贴操作会替换掉被选中的内容，如果没有内容被选中，则在光标位置插入这些内容。
- Save item：这个功能让你指定一个文件，把选中的请求和响应以 XML 的格式保存到这个文件，这里面包括所有的元数据如：响应的长度，HTTP 的状态码以及 MIME 类型。
- Don't intercept requests：通过这些命令可以快速地添加拦截动作的规则来阻止拦截到的消息，这些消息和当前的消息有着相同的特征(如远程主机、资源类型、响应编码)。
- Do intercept：仅对请求有效，这允许你可以对当请求和响应的进行强制拦截。
- Convert seiection：这些功能让你能够以多种方案对选择的文本进行快速的编码和解码。
- URL-encode as you type：如果这个选项被打开，你输入的像 & 和 = 这样的符号会被等价的 URL 编码代替。

#### 2、HTTP History
这个选项是来显示所有请求产生的细节，显示的有目标服务器和端口，HTTP 方法，URL ，以及请求中是否包含参数或被人工修改，HTTP 的响应状态码，响应字节大小，响应的 MIME 类型，请求资源的文件类型，HTML 页面的标题，是否使用 SSL ，远程 IP 地址，服务器设置的 cookies ，请求的时间。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.4.png)

双击某个请求即可打开详情,通过 Previous / next 可以快速切换请求，并且 Action 也可以将请求发送至其他模块。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.5.png)

可以通过最左边的列里的下拉菜单来加亮单个选项：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.6.png)

在历史记录表里，右击一个或多个选项，就会显示一个上下文菜单让你执行一些操作，包括修改目标范围，把这些选项发送到其他 Burp 工具，或者删除这些项：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.7.png)

还可以通过配置过滤器来确定哪些顶层的数据项显示在表格里。有效应用程序包含了大量的内容，如图像、CSS 等，这些有利于从视图上隐藏的。AJAX 应用程序产生大量相似的异步请求，你可能会想把他们从视图上过滤出来来查看一些感兴趣的项。在这个历史记录表的顶部有一个过滤栏。单击会有一个弹出窗口，让你来精准地配置显示哪些内容在表格里：

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.8.png)

#### 3、WebSockets history
这个选项主要用于记录 WebSockets 的数据包，是 HTML5 中最强大的通信功能，定义了一个全双工的通信信道，只需 Web 上的一个 Socket 即可进行通信，能减少不必要的网络流量并降低网络延迟。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.9.png)

#### 4、Options
该选项主要用于设置代理监听、请求和响应、拦截反应、匹配和替换、ssl 等，其中有八大选项：Proxy Listeners 、Intercept Client Requests 、Intercept Server Responses 、Intercept WebSockets Messages 、Response Modification 、Match and replace 、SSL Pass Through 、Miscellaneous。

##### 选项1：Proxy Listeners
代理侦听器是侦听从您的浏览器传入的连接本地 HTTP 代理服务器。它允许您监视和拦截所有的请求和响应，并且位于 BurpProxy 的工作流的心脏。默认情况下，Burp 默认监听 12.0.0.1 地址，端口 8080 。要使用这个监听器，你需要配置你的浏览器使用 127.0.0.1 ：8080 作为代理服务器。此默认监听器是必需的测试几乎所有的基于浏览器的所有 Web 应用程序。

##### 选项2：Intercept Client Requests
配置拦截规则，设置拦截的匹配规则。当 Intercept request based on the following rules 为选中状态时，Burpsuite 会配置列表中的规则进行拦截或转发。

*注意：如果该复选框未选中，那么即使 Intercept is on 也无法截取数据包。*

*规则可以通过 Enabled 列中的复选框选择开启或关闭。*

*规则可以是域名，IP 地址，协议，HTTP 方法，URL ，文件扩展名，参数，cookie ，头/主体内容，状态代码，MIME 类型，HTML 页面标题等。*

*规则按顺序处理，并且使用布尔运算符 AND 和 OR 组合。*

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.10.png)

###### Add：添加一个新的代理地址。
1、Binding：新建一个代理。`Bind to port：`- 绑定端口号
`Bind to address：`- 绑定ip地址。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.11.png)

2、Request handling：这些设置包括选项来控制是否 BurpSuite 重定向通过此侦听器接收到的请求：

- `Redirect to host：`- 如果配置了这个选项，Burp 会在每次请求转发到指定的主机，而不必受限于览器所请求的目标。需要注意的是，如果你正使用该选项，则可能需要配置匹配／替换规则重写的主机中的请求，如果服务器中，您重定向请求预期，不同于由浏览器发送一个主机头。
- `Redirect to port：`- 如果配置了这个选项，Burp 会在每次请求转发到指定的端口，而不必受限于浏览。
- Force use of SSL - 如果配置了这个选项，Burp 会使用 HTTPS 在所有向外的连接，即使传入的请求中使用普通的 HTTP 。您可以使用此选项，在与 SSL 相关的响应修改选项结合，开展 sslstrip 般的攻击使用 Burp ，其中，强制执行 HTTPS 的应用程序可以降级为普通的 HTTP 的受害用户的流量在不知不觉中通过 BurpProxy 代理。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.12.png)

3、Certificate：这些设置控制呈现给客户端的 SSL 服务器的 SSL 证书。

- Generate CA-signed per-host certificate - 这是默认选项。安装后，BurpSuite 创造了一个独特的自签名的证书颁发机构（CA）证书，并将此计算机上使用，每次 BurpSuite 运行。当你的浏览器发出 SSL 连接到指定的主机，Burp 产生该主机，通过 CA 证书签名的 SSL 证书。您可以安装 BurpSuite 的 CA 证书作为在浏览器中受信任的根，从而使每个主机的证书被接受，没有任何警报。您还可以导出其他工具或 Burp 的其他实例使用 CA 证书。
- `Generate a CA-signed certificate with a specific hostname：`- 这类似于前面的选项；然而，Burp 会产生一个单一的主机证书与每一个 SSL 连接使用，使用您指定的主机名。在进行无形的代理时，此选项有时是必要的，因为客户端没有发送连接请求，因此 Burp 不能确定 SSL 协议所需的主机名。你也可以安装 BurpSuite 的 CA 证书作为受信任的根。
- `Use a custom certificate：`- 此选项使您可以加载一个特定的证书（在 PKCS＃12 格式）呈现给你的浏览器。如果应用程序使用它需要特定的服务器证书（例如一个给定序列号或证书链）的客户端应该使用这个选项。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.13.png)

###### Edit：编辑选中的代理地址。
###### Remove：删除选中代理地址。
##### 选项3：Intercept Server Responses
配置拦截规则，设置拦截的匹配规则，不过这个选项是基于服务端拦截，当选小的 Intercept request based on the following rules 为选中状态时，Burpsuite 会匹配响应包。

##### 选项4：Intercept WebSockets Messages
##### 选项5：Response Modification

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.14.png)

##### 选项6：Match and Replace
用于自动替换请求和响应通过代理的部分。对于每一个 HTTP 消息，已启用的匹配和替换规则依次执行，选择适用的规则进行匹配执行。

规则可以分别被定义为请求和响应，对于消息头和身体，并且还特别为只请求的第一行。每个规则可以指定一个文字字符串或正则表达式来匹配，和一个字符串来替换它。对于邮件头，如果匹配条件，整个头和替换字符串匹配留空，然后头被删除。如果指定一个空的匹配表达式，然后替换字符串将被添加为一个新的头。有可协助常见任务的各种缺省规则 - 这些都是默认为禁用。匹配多行区域，您可以使用标准的正则表达式语法来匹配邮件正文的多行区域。

##### 选项7：SSL Pass Through

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.15.png)

##### 选项8：Miscellaneous

![](https://github.com/TWater/BurpSuite/raw/master/Picture/1.16.png)

## Target 模块（目标模块）
### Target 功能
目标工具包含了 Site map ，用你的目标应用程序的详细信息。它可以让你定义哪些对象在范围上为你目前的工作，也可以让你手动测试漏洞的过程，Target 分为 Site map 和 Scope 两个选项卡。

#### 选项一、Site map
Site map 会在目标中以树形和表形式显示，并且还可以查看完整的请求和响应。树视图包含内容的分层表示，随着细分为地址、目录、文件和参数化请求的 URL 。您还可以扩大有趣的分支才能看到进一步的细节。如果您选择树的一个或多个部分，在所有子分支所选择的项目和项目都显示在表视图。

该表视图显示有关每个项目（URL ，HTTP 状态代码，网页标题等）的关键细节。您可以根据任意列进行排序表（单击列标题来循环升序排序、降序排序和未排序）。如果您在表中选择一个项目，请求和响应（如适用）该项目显示在请求／响应窗格。这包含了请求和响应的 HTTP 报文的编辑器，提供每封邮件的详细分析。

站点地图汇总所有的信息 BurpSuite 已经收集到的有关申请。这包括：

- 所有这一切都通过代理服务器直接请求的资源。
- 已推断出通过分析响应代理请求的任何物品（前提是你没有禁用被动 Spider ）。
- 内容使用 Spider 或内容发现功能查找。
- 由用户手动添加的任何项目，从其它工具的输出。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.1.png)

这样看起来 Site map 是不是很乱，则可以右击 Add to scope ，然后点击 Filter 勾选 Show only in-scope items ，此时你再回头看 Site map 就只有百度一个地址了。这里 Filter 可以过滤一些参数，Show all 显示全部，Hide all 隐藏所有，如果勾选了表示不过滤。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.2.png)

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.3.png)

选择之后就只剩下一个网址了。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.4.png)

针对地址右击显示当前可以做的一些动作操作等功能。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.5.png)

#### 选项二、Scope
这个主要是配合 Site map 做一些过滤的功能。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.6.png)

已请求在 Site map 中的项目会显示为黑色，尚未被请求的项目显示为灰色。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/2.7.png)

## Spider 模块（蜘蛛爬行）
### 一、简介
Burp Spider 是一个映射 web 应用程序的工具。它使用多种智能技术对一个应用程序的内容和功能进行全面的清查。

Burp Spider 通过跟踪 HTML 和 JavaScript 以及提交的表单中的超链接来映射目标应用程序，它还使用了一些其他的线索，如目录列表、资源类型的注释以及 robots.txt 文件。结果会在站点地图中以树和表的形式显示出来，提供了一个清楚并非常详细的目标应用程序视图。

Burp Spider 能使你清楚地了解到一个 web 应用程序是怎样工作的，让你避免进行大量的手动任务而浪费时间。在跟踪链接、提交表单、精简 HTNL 源代码上，可以快速地确认应用程序的潜在的脆弱功能，还允许你指定特定的漏洞，如 SQL 注入、路径遍历。

### 二、模块介绍
要对应用程序使用 Burp Spider 需要两个简单的步骤：

1. 使用 Burp Proxy 配置为你浏览器的代理服务器，浏览目标应用程序（为了节省时间，你可以关闭代理拦截）。
2. 到站点地图的 "Target" 选项上，选中目标应用程序驻留的主机和目录。选择上下文菜单的 "Spider this host／branc" 选项。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.1.png)

#### 选项一、Control
用来开始和停止 Burp Spider ，监视它的进度，以及定义 spidering 的范围。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.2.png)

#### 选项二、Options
这个选项里包含了许多控制 Burp Spider 动作的选项。

1、Crawler Settings

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.3.png)

- Check robots.txt ：检测 robots.txt 文件，选择后 Burp Spider 会要求和处理 robots.txt 文件，提取内容链接。
- Detect custom "not found" responses ：检测自定义的 "not found" 响应。打开后 Burp Spider 会从每个域请求不存在的资源，编制指纹与诊断 "not found" 响应其它请求检测自定义 "not found" 的响应。
- Ignore links to non-text content ：忽略非文本内容的连接。这个选项被选中，Spider 不会请求非文本资源。使用这个选项，会减少 spidering 时间。
- Request the root of all directories ：请求所有的根目录。如果这个选项被选中，Burp Spider 会请求所有已确认的目标范围内的 web 目录，如果在这个目标站点存在目录遍历，这选项将是非常的有用。
- Make a non-parameterized request to each dynamic page ：对每个动态页面进行非参数化的请求。如果这个选项被选中，Burp Spider 会对在范围内的所有执行动作的 URL 进行无参数的 GET 请求。如果期待的参数没有被接收，动态页面会有不同的响应，这个选项就能成功地探测出额外的站点内容和功能。
- Maximum link depth ：这是 Burp Suite 在种子 URL 里的浏览 "hops" 的最大数。0 表示让 Burp Suite 只请求种子 URL 。如果指定的数值非常大，将会对范围内的链接进行无限期的有效跟踪。将此选项设置为一个合理的数字可以帮助防止循环 Spider 在某些种类的动态生成的内容。
- Maximum parameterized requests per URL ：该蜘蛛用不同的参数请求相同的基本 URL 的最大数目。将此选项设置为一个合理的数字可以帮助避免爬行 “无限” 的内容。

2、Passive Spidering

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.4.png)

- Passively spider as you browse ：如果这个选项被选中，Burp Suite 会被动地处理所有通过 Burp Proxy 的 HTTP 请求，来确认访问页面上的链接和表格。使用这个选项能让 Burp Spider 建立一个包含应用程序内容的详细画面，甚至此时你仅仅使用浏览器浏览了内容的一个子集，因为所有被访问内容链接到内容都会自动地添加到 Suite 的站点地图上。
- Link depth to associate with Proxy requests ：这个选项控制着与通过 Burp Proxy 访问的 web 页面有关的 "link depth" 。为了防止 Burp Spider 跟踪这个页面里的所有链接，要设置一个比上面选项卡里的 "Maximum link depth" 值还高的一个值。

3、Form Submission

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.5.png)

- Individuate forms by ：个性化的形式。这个选项是配置个性化的标准（执行 URL 、方法、区域、值）。当 Burp Spider 处理这些表格时，它会检查这些标准以确认表格是否是新的。旧的表格不会加入到提交序列。
- Don’t submit forms ：开启后蜘蛛不会提交任何表单。
- Prompt for guidance ：提醒向导。如果被选中，在你提交每一个确认的表单前，Burp Suite 都会为你指示引导。这允许你根据需要在输入域中填写自定义的数据，以及选项提交到服务器的哪一个区域。
- Automatically submit using the following rules to assign text field values ：自动提交。如果选中，Burp Spider 通过使用定义的规则来填写输入域的文本值来自动地提交范围内的表单。每一条规则让你指定一个简单的文本或者正则表达式来匹配表单字段名，并提交那些表单名匹配的字段值。
- Set unmatched fields to ：设置不匹配的字段。

4、Application Login

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.6.png)

- Don't submit login forms ：不提交登录表单。开启后 Burp 不会提交登录表单。
- Prompt for guidance ：提示向导。Burp 能交互地为你提示引导。默认设置项。
- Handle as ordinary forms ：以一般形式处理。Burp 通过你配置的信息和自动填充规则，用处理其他表单的方式来处理登陆表单。
- Automatically submit these credentials ：自动提交自定义的数据。开启后 Burp 遇到登录表单会按照设定的值进行提交。

5、Spider Engine

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.7.png)

- Number of threads ：设置请求线程。控制并发请求数。
- Number of retries on network failure ：如果出现连接错误或其他网络问题，Burp 会放弃和移动之前重试的请求指定的次数。测试时，间歇性网络故障是常见的，所以最好是在发生故障时重试该请求了好几次。
- Pause before retry（milliseconds）：当重试失败的请求，Burp 会等待指定的时间（以毫秒为单位）以下，然后重试失败。如果服务器宕机、繁忙或间歇性的问题发生，最好是等待很短的时间，然后重试。
- Throttle between requests（milliseconds）：在每次请求之前等待一个指定的延迟（以毫秒为单位）。此选项很有用，以避免超载应用程序，或者是更隐蔽。
- Add random variations to throttle ：添加随机的变化到请求中。增加隐蔽性。

6、Request Headers
您可以配置头蜘蛛在请求中使用的自定义列表。这可能是有用的，以满足各个应用程序的特定要求。例如，测试设计用于移动设备的应用程序时，以模拟预期的用户代理。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/3.8.png)

- Use HTTP version 1.1 ：在蜘蛛请求中使用 HTTP／1.1 ，不选中则使用 HTTP/1.0 。
- Use Referer header ：当从一个页面访问另一个页面是加入 Referer 头，这将更加相似与浏览器访问。

## Scanner 模块（漏洞扫描）
### 一、简介
Burp Scanner 是一个进行自动发现 web 应用程序的安全漏洞的工具。它是为渗透测试人员设计的，并且它和你现有的手动执行进行的 web 应用程序半自动渗透测试的技术方法很相似。

使用的大多数的 web 扫描器都是单独运行的：你提供了一个开始 URL ，单击“ go ”，然后注视着进度条的更新直到扫描结束，最后产生一个报告。Burp Scanner 和这完全不同，在攻击一个应用程序时它和你执行的操作紧紧的结合在一起。让你细微控制着每一个扫描的请求，并直接反馈回结果。

Burp Scanner 可以执行两种扫描类型：主动扫描（ Active scanning ）、被动扫描（ Passive scanning ）。

### 二、模块说明
#### 1、Issue activity

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.1.png)

#### 2、Scan queue
扫描队列，这里将显示扫描队列的状态进度结果等。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.2.png)

主要包含以下内容：

1. 索引号的项目，反映该项目的添加顺序。
2. 目的地协议，主机和 URL 。
3. 该项目的当前状态，包括完成百分比。
4. 项目扫描问题的数量（这是根据所附的最严重问题的重要性和彩色化）。
5. 在扫描项目的请求数量进行。
6. 网络错误的数目遇到的问题。
7. 为项目创建的插入点的数量。

#### 3、Live scanning
实时扫描可让您决定哪些内容通过使用浏览器的目标应用，通过 BurpProxy 服务器进行扫描。您可以实时主动扫描设定 Live Active Scanning（积极扫描）和 Live Passive Scanning（被动扫描）两种扫描模式。

Live Active Scanning：积极扫描。当浏览时自动发送漏洞利用代码。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.3.png)

Live Passive Scanning：被动扫描。只分析流量不发送任何请求。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.4.png)

#### 4、Issue definitions
漏洞列表，列出了Burp可以扫描到的漏洞详情。

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.5.png)

#### 5、Options
包含Burp扫描选项进行攻击的插入点、主动扫描引擎、主动扫描优化、主动扫描区和被动扫描区域。

##### 1、Attack Insertion Points

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.6.png)

##### 2、Active Scanning Engine

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.7.png)

##### 3、Active Scanning Optimization

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.8.png)

##### 4、Active Scanning Areas

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.9.png)

##### 5、Passive Scanning Areas

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.10.png)

##### 6、Static Code Analysis

![](https://github.com/TWater/BurpSuite/raw/master/Picture/4.11.png)