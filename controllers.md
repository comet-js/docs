category: Fundamentals
title: Controllers
description: Controllers handle all the incoming requests logic and the outgoing responses.
------

The simplest and easiest way to create a CometJS application is by using our command-line interface tool.

## Controllers Creation

You have two methods to create a controller. The fastest way is by using our CLI tools by running the `comet make:controller <name>` command in your terminal. All the controllers created using this command are stored in the `/controllers` directory. You can also create your controllers manually by following the same structure as the example below.

```ts
import { BaseController, Controller, Get, Request, Response, json } from "cometjs";

@Controller("users")
export class UserController extends BaseController {

  @Get("users.show", "/[id]", { id: /^\\d+$/ })
  show(request: Request, response: Response): void {
    return json(UserService.get(request.parameters.id));
  }

  @Get("users.list", "/list")
  list(request: Request, response: Response): void {
    return json(UserService.all());
  }

}
```
