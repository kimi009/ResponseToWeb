# ResponseToWeb
upload file to server  after then download by brower


var virtualDirectoryPath = "~/../downloads"
var physicalDirectory = HttpContext.Current.Server.MapPath(virtualDirectoryPath);
//路径不存在就创建新的路径
//获取网络路径
var abs=VirtualPathUtility.ToAbsolute(virtualDirectoryPath);
var url = new System.Uri(Request.RequestUri,abs).AbsoluteUri;

//创建响应报文
HttpResponseMessage response=Request.CreateResponse(HttpStatusCode.Ok);
response.Content=new StringContent(url+"/"+filename);
response.Content.Headers.ContentDisposition = new ContentDispositionHeaderValue("attachment"){}
