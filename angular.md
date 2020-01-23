### Route in angular 6
// onSameUrlNavigation: 'reload'

pages are component in angular

router-outlet
Routes and paths
Navigation

##### points:
router-outlets, path matching stratergies, route parameter, route guard

Q. difference between Routes and paths?

Angular Router

<router-outlet></router-outlet> gets matched based on current url ; navigate to current route
<a [routerLink]="'/contacts'"></a> ; navigate to diffferent route
Route : An Object comprised of atleast a path and a component/ redirectTo path

wildcard string ** in path can be used to display not found view.

ROUTE MATCHING STRATEGIES:
pathMatch: 'prefix' // by default
{ path:  'contacts',pathMatch: 'prefix', component:  ContactListComponent}
is same as 
{ path:  'contacts', component:  ContactListComponent}


Route param:
Angular Router allows you to access parameters in different ways:
1.  ActivatedRoute service . 2.  ParamMap observable 

ROUTE GUARDS :  CanActivate 

e.g. { path:  'contacts/:id, canActivate:[MyGuard], component:  ContactDetailComponent}

params : Observable<Params> : An observable of the matrix parameters scoped to this route.
queryParams : Observable<Params> : An observable of the query parameters shared by all the routes.

outlet: string : The outlet name of the route, a constant.

### angular change detection

https://indepth.dev/a-gentle-introduction-into-change-detection-in-angular/
dirty checking : By default, Angular makes no assumption on what the component depends upon.
So it has to be conservative and will checks every time something may have changed.
ChangeDetectionStrategy.Default : 
It will perform checks for each browser events, timers, XHRs and promises.
ChangeDetectionStrategy.onPush
components internally are represented as views
Change Detection : updates new value to binding, then to oldValues array
