1. 一些有用的全局变量

	    #define IS_IPAD (UI_USER_INTERFACE_IDIOM() == UIUserInterfaceIdiomPad)
	    #define IS_IPHONE (UI_USER_INTERFACE_IDIOM() == UIUserInterfaceIdiomPhone)
	    #define IS_RETINA ([[UIScreen mainScreen] scale] >= 2.0)

	    #define SCREEN_WIDTH ([[UIScreen mainScreen] bounds].size.width)
	    #define SCREEN_HEIGHT ([[UIScreen mainScreen] bounds].size.height)
	    #define SCREEN_MAX_LENGTH (MAX(SCREEN_WIDTH, SCREEN_HEIGHT))
	    #define SCREEN_MIN_LENGTH (MIN(SCREEN_WIDTH, SCREEN_HEIGHT))

	    #define IS_IPHONE_4_OR_LESS (IS_IPHONE && SCREEN_MAX_LENGTH < 568.0)
	    #define IS_IPHONE_5 (IS_IPHONE && SCREEN_MAX_LENGTH == 568.0)
	    #define IS_IPHONE_6 (IS_IPHONE && SCREEN_MAX_LENGTH == 667.0)
	    #define IS_IPHONE_6P (IS_IPHONE && SCREEN_MAX_LENGTH == 736.0)


2. url encode

	    NSString *urlString = [NSString stringWithFormat:@"%@", self.text];
	    NSString *escapedUrl = [urlString stringByAddingPercentEscapesUsingEncoding:NSUTF8StringEncoding];
	    [[UIApplication sharedApplication] openURL:[NSURL URLWithString:escapedUrl]];

3. 跳转
	
	    ResultViewController *vc = [self.storyboard instantiateViewControllerWithIdentifier:@"ResultViewController"];
	    vc.text = [self.history objectAtIndex:indexPath.row];
	    vc.isShowHistoryBtn = NO;
	    [self.navigationController pushViewController:vc animated:YES];

4. uitableviewcell static

	    -(UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
	    {
	    	NSInteger section = indexPath.section;
	    	NSInteger row = indexPath.row;
	    	UITableViewCell *cell = [super tableView:tableView cellForRowAtIndexPath:indexPath];
    
	    	return cell;
	    }
